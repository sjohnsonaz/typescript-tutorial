# New TypeScript Project

Creating a TypeScript project is easy!

Let's get up and running with build and testing scripts!

You will need a few things first:

- Install **Node.js** from [nodejs.org](https://nodejs.org/).
- Install an editor, for example **Visual Studio Code** from [code.visualstudio.com](https://code.visualstudio.com/)
- Open a **terminal**, and get ready!

## Create your project folder

Create a folder with your project's name in `[[Project Name]]`.

> **NOTE:** Node.js convention is to use `kebab-case`. All letters are lower case, and dashes are used for spaces.

Run the following command:

```bash
mkdir [[Project Name]]
```

### Open with an Editor

The following example is for Visual Studio Code. It will likely be similar for other editors.

Open your folder in Visual Studio Code. Open Visual Studio Code, then navigate to **File** -> **Open Folder...**.

Alternatively, if you have the shortcut set up, you can run the following command:

```bash
code [[Project Name]]
```

Once in the editor, open the **Integrated Terminal** to continue. Navigate to **View** -> **Terminal**, or use the Keyboard Shortcut `` Ctrl + ` `` or `` Cmd + ` ``.

### Continue in the system terminal

Alternatively, change directory into the folder in the current terminal:

```bash
cd [[Project Name]]
```

## Install Dependencies

Create your `package.json`, which stores **NPM** configuration.

> **NOTE:** When prompted, it is HIGHLY recommended to start with version `0.0.0` or `0.0.1`.
>
> This implies that the project is in development. Starting with `1.0.0` implies the project is **stable**.

Run the following command:

```bash
npm init
```

Install **TypeScript** and **Jest** as `"devDependencies"` in `package.json`. This will also create a `package-lock.json` file, which stores specific package version information.

Run the following command:

```bash
npm i -D typescript jest ts-jest @types/jest
```

## Configure TypeScript

Creates your `tsconfig.json` file, which stores TypeScript configuration.

Run the following command:

```bash
npx tsc --init
```

Creates your `src/index.ts` file.

Run the following commands:

```bash
mkdir src
touch ./src/index.ts
```

In `tsconfig.json`, update the following `"compilerOptions"`. This configures TypeScript to use your source files, and generate all of the necessary declaration and map files.

```bash
  "rootDir": "./src",
  "declaration": true,
  "declarationMap": true,
  "sourceMap": true,
  "outDir": "./dist",
```

In `package.json`, create the following properties. This configures your package to use the TypeScript generated files.

```bash
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
```

## Configure Scripts

In `package.json`, create the following `"scripts"`. These are common scripts for building and testing.

```bash
  "scripts": {
    "test": "jest",
    "start": "tsc --watch",
    "build": "tsc",
    "clean": "tsc --build --clean"
    "prepublishOnly": "tsc --build --clean && tsc",
  }
```

In `package.json`, add the following section. This tells Jest how to find and run your TypeScript tests.

```bash
  "jest": {
    "preset": "ts-jest",
    "testPathIgnorePatterns": [
      "<rootDir>/dist/"
    ]
  }
```

## Configure Git

Create your Git configuration. It is important to check in only source files.

Run the following commands:

```bash
git init
touch .gitignore
```

Add the following to `.gitignore`. This will prevent checking in TypeScript generated files.

```bash
node_modules/
dist/
```

## Configure NPM publish

Create your NPM publish configuration. It is important to publish BOTH source files, and TypeScript generated files.

Run the following command:

```bash
touch .npmignore
```

Add the following to `.npmignore`. This will prevent checking in unnecessary files.

> **NOTE:** Do not include `dist/` or `src/` in your `.npmignore` file.

```bash
tsconfig.json
.gitignore
.npmignore
```
