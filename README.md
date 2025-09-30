# sanity-plugin-workspace-home-esm

This is a fork of official Sanity plugin, with a resolve to the ESM modules in components 

This plugin adds a "Home" Tool to your Studio with a listing of all available workspaces. Useful as the first page of your Studio to quickly navigate to the workspace of your choice.

![plugin inside sanity studio showing workspaces](https://user-images.githubusercontent.com/9684022/227136123-ec1908dd-fc60-4832-9079-6f5ed5892923.png)

## Installation

```sh
npm install @oleg1357/sanity-plugin-workspace-home-esm
```

## Usage

For simple installation, import the predefined workspace config from the plugin and use it as the first config in your `sanity.config.ts` (or .js) file.

```ts
import {defineConfig} from 'sanity'
import {workspaceHomeConfig} from 'sanity-plugin-workspace-home'

export default defineConfig([
  workspaceHomeConfig({
    // projectId and dataset are required, but not used by the plugin
    projectId: 'replace-with-your-project-id',
    dataset: 'replace-with-your-dataset-name',    
  }),
  // ...all other workspaces
])
```

Alternatively, define your own workspace config for the plugin. This plugin is designed to be used in a workspace where it is the only plugin. This should be the first workspace configured in `sanity.config.ts` (or .js).

```ts
import {defineConfig} from 'sanity'
import {workspaceHome} from 'sanity-plugin-workspace-home'

export default defineConfig([{
  {
    name: 'home',
    title: 'Home',
    basePath: '/home',
    icon: HomeIcon,
    plugins: [workspaceHome()],
    // projectId and dataset are required, but not used by the plugin
    projectId: 'replace-with-your-project-id',
    dataset: 'replace-with-your-dataset-name',
  },
  // ...all other workspaces
}])
```

## License

[MIT](LICENSE) © Sanity

## Develop & test

This plugin uses [@sanity/plugin-kit](https://github.com/sanity-io/plugin-kit)
with default configuration for build & watch scripts.

See [Testing a plugin in Sanity Studio](https://github.com/sanity-io/plugin-kit#testing-a-plugin-in-sanity-studio)
on how to run this plugin with hotreload in the studio.


### Release new version

Run ["CI & Release" workflow](TODO/actions/workflows/main.yml).
Make sure to select the main branch and check "Release new version".

Semantic release will only release on configured branches, so it is safe to run release on any branch.
