# Create React App DevOps

See the app live at: https://testing-devops-v2.now.sh/

Looking for v1 that uses IBM Cloud (Bluemix)? Check it out [here](https://github.com/seejamescode/testing-devops-v2/tree/v1).

This is a repo that proves how easily it is to implement automated builds, Node servers, and Express APIs around [Create React App](https://github.com/facebookincubator/create-react-app). In this repo, we do the following (broken up by commits):

1.  [Use Create React App to get the UI up](https://github.com/seejamescode/testing-devops-v2/commit/464ea1bdef0ba6dd1445456c8b88633fe927b212)
2.  [Setup Your server with Node, Express, and Babel](https://github.com/seejamescode/testing-devops-v2/commit/56b428a66837ed754ed4778007771ca582d56940)
3.  [Run the app on the web with Zeit Now](https://github.com/seejamescode/testing-devops-v2/commit/2b576c9b305462128b1daab0fe0e2b6108e53aed)
4.  [Fetch API data while keeping secrets secure](https://github.com/seejamescode/testing-devops-v2/commit/3ce5279b9ad33e82f3ccf397af146580b099d5d9)
5.  [Automatic deployment from master branch pushes and tag releases using GitHub and Travis CI](https://github.com/seejamescode/testing-devops-v2/commit/d9931232a2419d97535b0879481c4467a1382d08)

This project was inspired by [Create React PWA](https://github.com/jeffposnick/create-react-pwa) -a project that explains how to upgrade your Create React App project to a Progressive Web App.

## Fork Instructions

1.  Create accounts at [Zeit](https://zeit.co/) (for app hosting), [Github](https://github.com) (for code hosting), and [Travis CI](https://travis-ci.org/) (for autodeployment).

2.  Install on your machine [Zeit Now Desktop](https://zeit.co/download), [Node](https://docs.npmjs.com/getting-started/installing-node), and [Yarn](https://yarnpkg.com/lang/en/docs/install/#mac-tab).

3.  [Fork this repo in the top right corner and create a local clone to your computer](https://help.github.com/articles/fork-a-repo/)

4.  Change `testing-devops-v2` to a unique app name at:

- [.travis.yml](https://github.com/seejamescode/testing-devops-v2/blob/master/.travis.yml#L11) (Keep the `-staging` when you see it.)
- [now.json](https://github.com/seejamescode/testing-devops-v2/blob/master/now.json#L2)
- [package.json](https://github.com/seejamescode/testing-devops-v2/blob/master/package.json#L2) (There are six instances in this file. Keep `-staging` when you see it.)

5.  Request a new [personal access token](https://github.com/settings/tokens/new) with repo scope from GitHub and create a `now-secrets.json` file at the root of the repo like `{ "@github": "YOUR_ACCESS_TOKEN" }`. This file will be [gitignored](https://help.github.com/articles/ignoring-files/), so it will never end up on GitHub to keep your token secure.

6.  Run `now secret add github YOUR_ACCESS_TOKEN` so that Zeit Now knows your access token without receiving the secrets file.

7.  Run `now && now alias` to push the production version of your app. This is the app that will be updated everytime you do a GitHub release and should be live at `YOURAPPNAME.now.sh`.

8.  Run `now && now alias YOURAPPNAME-staging` to push the staging version of your app. Notice that `YOURAPPNAME` should be the unique app name you chose earlier. This is the app that will be updated when you push to the master branch and should be live at `YOURAPPNAME-staging.now.sh`.

9.  Get a token at [Zeit](https://zeit.co/account/tokens). Then go to [Travis CI](https://travis-ci.org/), activate the repo, and add an environment variable called `NOW_TOKEN` with the token value you just received.

To recap what we have done: First, we quickly got our React project configured thanks to Create React App. Then we built a simple server that can use any [Babel](https://babeljs.io/docs/en) presets and plugins you want to add to `package.json`. We pushed the app into the world in two data centers in America and Europe in case one goes down. Next, we got Travis deploying the app (with zero downtime) for any of our changes. We also set up a staging app so that we could test pre-releases that are pushed to the master branch of GitHub.

I hope this project has helped make your workflow easier as you make epic web apps! A big 🙏 goes to the contributors of [Babel](https://github.com/babel/babel/graphs/contributors), [Create React App](https://github.com/facebookincubator/create-react-app/graphs/contributors), [Express](https://github.com/expressjs/express/graphs/contributors), [Node](https://github.com/nodejs/node/graphs/contributors), and all other packages used. Also, all the ❤️️ goes to Zeit, Github, and Travis CI for their free tiers.
