# Shopify CLI 3.X workshop

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat&colorA=338fbb&colorB=1c1c1c&logoColor=ffffff)](https://github.com/odestry/.github/blob/main/CONTRIBUTING.md)
[![Discord Shield](https://img.shields.io/discord/983602196493004820?style=flat&colorA=338fbb&colorB=1c1c1c&label=discord&logo=discord&logoColor=ffffff)](https://discord.gg/blanklob-community-983602196493004820)

[Tutorial](#tutorial) |
[Getting started](#getting-started) |
[Caveats](#caveats) |
[Contributing](#contributing) |
[About](#about) |
[License](#license)

> Please note that Shopify might change this in the future, so you might wanna check if Shopify implimented a better way to handle mutlitple enviroments natively before using this work-around.

## Tutorial

[![Tutoria about How to use Shopify CLI 3.0 for Theme Development and deploy themes to different stores.](https://img.youtube.com/vi/keRtZNx_cco/0.jpg)](https://www.youtube.com/watch?v=keRtZNx_cco)

An overview of the Shopify CLI 3.0 and how to use it with themes and to deploy themes programmatically to multiple stores, please keep in mind that you can still use Shopify Github integration to handle deployment. I also introduced Shopify CLI plugins, a cool feature to extend it and make it more personalized depending on your needs.

## Getting started

Before getting started, make sure you migrate to the lastest Shopify CLI 3.X version at least 3.2.0 and you are using 14 node version or above, to avoid any issues.

- Shopify CLI 3.X
- Node 14.0.0 or above

Here is the Shopify CLI 3.0 [migration guide](https://shopify.dev/themes/tools/cli/migrate) for more informations.

### Clone the theme

You can clone the project using either the git clone commande or the Shopify theme init command.

```bash
shopify theme init -u https://github.com/blanklob/shopify-cli-3-themes-demo 
# or 
git clone https://github.com/blanklob/shopify-cli-3-themes-demo demo-store 
```

Then cd into the project folder.

### Install the dependencies

Once first step is done, start by installing the dependencies, with either yarn, npm, or pnpm

```bash
npm install
```

### Replace the naming of the configuration files

Once the second step is done all you have to do is remove the `.tpl` keyword in the file, or create a new file, without the tpl, the new file will be ignored by git, and start filling it with proper enviroments variable values.

### Replace the enviroment variables in the configuration files

Choose which configuration file you want to choose, by default it's the `shopify.presets.json` json version, then replace all enviroement variables with proper values, mainly these values for each enviroment, and you can also remove or change enviroments name in the configuration, just make sure you do the same in the `package.json` scripts part after the `-e` flag.

Supported enviroments variables:

- `SHOPIFY_CLI_THEME_TOKEN` : This is a private token, can be claimed using the [Theme Access Shopify Public](https://apps.shopify.com/theme-access) app. (required for programatic use)
- `SHOPIFY_FLAG_STORE` : The store handle or url example: blanklob.myshopify.com or just blanklob. (required for programatic use)
- `SHOPIFY_FLAG_THEME_ID` : the name or the theme id that you want push to, if the theme deosn't exist make sure you add `-u` flag to the commande, so Shopify CLI will create a new theme. (required for programatic use)
- `SHOPIFY_FLAG_PATH` : The path to theme folder. Default '.' an example would be: './dist'

> Make sure you don't commit your presets file to github, or add secrets to package.json, the `SHOPIFY_CLI_THEME_TOKEN` is a private token, that should not be shared publicly.

## Caveats

There are some few caveats to this workflow, the first is that the `shopify theme dev` command deosn't support `--password` flag which means it deosn't support programtic auth, you need to authenticate every 90 minutes, to use the command on a specific store, this is one of the few issues that are discussed in the Shopify CLI 3.0 repo. Check refrences below for more informations.

### References

- Add support for theme password flag in dev command in the Shopify CLI [bug issue](https://github.com/Shopify/cli/issues/695).

## Contributing

We'd love your help! Please read our [contributing guide](https://github.com/odestry/.github/blob/main/CONTRIBUTING.md) to learn about our development process, how to propose bug fixes and improvements.

## About

Odestry isn't just a community; it's a group of dedicated folks all aiming to build better commerce together. Our mission is to create a supportive and open space where anyone, regardless of experience, can connect, learn, and grow. Here, you'll get inspired, have real talks, and find plenty of resources and open source tools to help you build. Whether you're looking to network, find opportunities, or just have meaningful conversations, join us and be part of a community that values authenticity, collaboration, and innovation. [Learn more](https://odestry.com).

## License

Copyright (c) 2024-present Odestry. See [LICENSE](/LICENSE.md) for further details.
