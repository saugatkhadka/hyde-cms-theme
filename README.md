# Victor Hugo CMS Template
<!-- Markdown snippet -->
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/saugatkhadka/hyde-cms-theme)

![hyde theme image](https://s3-us-west-1.amazonaws.com/publis-brian-images/hyde.png)

**A [Hugo](http://gohugo.io/) boilerplate for creating truly epic websites**

This is a boilerplate for using Hugo as a static site generator and Gulp + Weback as your
asset pipeline.

It's setup to use post-css and babel for CSS and JavaScript.

## Usage
Be sure that you have the latest node, npm and [Hugo](https://gohugo.io/overview/installing/) installed. If you need to install hugo, run:

Clone this repository and run:

```bash
npm install
npm start
```

Then visit http://localhost:3000/ - BrowserSync will automatically reload CSS or
refresh the page when stylesheets or content changes.

To build your static output to the `/dist` folder, use:

```bash
npm run build
```

## Structure

```
|--site                // Everything in here will be built with hugo
|  |--content          // Pages and collections - ask if you need extra pages
|  |--data             // YAML data files with any data for use in examples
|  |--layouts          // This is where all templates go
|  |  |--partials      // This is where includes live
|  |  |--index.html    // The index page
|  |--static           // Files in here ends up in the public folder
|--src                 // Files that will pass through the asset pipeline
|  |--css              // CSS files in the root of this folder will end up in /css/...
|  |--js               // app.js will be compiled to /js/app.js with babel
```
## CMS

### How it works

Netlify CMS is a single-page app that you pull into the `/admin` part of your site.

It presents a clean UI for editing content stored in a Git repository.

You setup a YAML config to describe the content model of your site, and typically
tweak the main layout of the CMS a bit to fit your own site.

### Setup GitHub as a Backend

In the `config.yml` file [change the GitHub owner and repo](https://github.com/bdougie/strata-cms-template/blob/master/site/static/admin/config.yml#L3) to reflect your repo:

```yaml
backend:
  name: github
  repo: owner/repo # Path to your Github repository
  branch: master # Branch to update (master by default)
  
  ...
```
When a user navigates to `/admin` she'll be prompted to login, and once authenticated
she'll be able to create new content or edit existing content.
The default Github-based authenticator integrates with Netlify's [Authentication Provider feature](https://www.netlify.com/docs/authentication-providers) and the repository
backend integrates directly with Github's API.

To get everything hooked up, setup continuous deployment from Github to Netlify
and then follow [the documentation](https://www.netlify.com/docs/authentication-providers)
to setup Github as an authentication provider.

That's it, now you should be able to go to the `/admin` section of your site and
log in.

### Find out more and contribute

Visit the [Netlify CMS](https://github.com/netlify/netlify-cms/) to find out more and contribute. 

## Basic Concepts

You can read more about Hugo's template language in their documentation here:

https://gohugo.io/templates/overview/

The most useful page there is the one about the available functions:

https://gohugo.io/templates/functions/

For assets that are completely static and don't need to go through the asset pipeline,
use the `site/static` folder. Images, font-files, etc, all go there.

Files in the static folder ends up in the web root. So a file called `site/static/favicon.ico`
will end up being available as `/favicon.ico` and so on...

The `src/js/app.js` file is the entrypoint for webpack and will be built to `/dist/app.js`.

You can use ES6 and use both relative imports or import libraries from npm.

Any CSS file directly under the `src/css/` folder will get compiled with [PostCSS Next](http://cssnext.io/)
to `/dist/css/{filename}.css`. Import statements will be resolved as part of the build

## Deploying to netlify

- Push your clone to your own GitHub repository.
- [Create a new site on Netlify](https://app.netlify.com/start) and link the repository.

Now netlify will build and deploy your site whenever you push to git.

##  Enjoy!!

#### License

[MIT](LICENSE)
