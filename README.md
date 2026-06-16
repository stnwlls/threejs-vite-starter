# Three.js Vite Starter

A minimal Three.js + Vite starter with the setup I usually want before building a scene.

## Prerequisites

You need Node.js and npm installed before using this starter. npm is used to install dependencies and run the project scripts.

npm ships with Node.js. Choose the install method you prefer from the official docs:

- [Node.js downloads](https://nodejs.org/en/download)
- [npm install docs](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

Check that both commands work:

```bash
node --version
npm --version
```

This starter uses Vite for the dev server and production build. Vite is installed locally from `package.json` when you run `npm install`; you do not need to install Vite globally.

Learn more about Vite:

- [Vite website](https://vite.dev/)
- [Vite guide](https://vite.dev/guide/)

This starter is built with Three.js. Credit to the Three.js project for the rendering library this setup is based on.

Learn more about Three.js:

- [Three.js website](https://threejs.org/)
- [Three.js docs](https://threejs.org/docs/)

## Use This Starter

Clone the repo:

```bash
git clone https://github.com/stnwlls/threejs-vite-starter.git
cd threejs-vite-starter
```

Install dependencies:

```bash
npm install
```

Start the dev server:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

## What Is Included

- Vite
- Three.js
- `canvas#app`
- `src/app.js`
- `src/style.css` with a small reset
- `public/textures/` for texture files
- `OrbitControls` with damping enabled
- `TextureLoader`
- `lil-gui`
- `THREE.SRGBColorSpace`
- capped pixel ratio with `Math.min(window.devicePixelRatio, 2)`
- `THREE.Timer` and `deltaTime`
- section comments for easy refactoring later

There is no `vite.config.js` by default because this starter does not need custom Vite settings. Add one later if you need aliases, plugins, a custom `base`, dev server settings, or build settings.

## File Structure

```txt
.
|-- .gitignore
|-- README.md
|-- index.html
|-- package-lock.json
|-- package.json
|-- public/
|   `-- textures/
|-- scripts/
|   `-- threejs
`-- src/
    |-- app.js
    `-- style.css
```

## App Structure

`src/app.js` is intentionally kept as one file. The sections are marked like this:

```js
/**
 * Section
 */
```

The starter sections are:

- Debug
- Canvas
- Scene
- Textures
- Camera
- Renderer
- Controls
- Resize
- Animate

When the project grows, those sections can be split into separate files like `camera.js`, `renderer.js`, `controls.js`, or `textures.js`.

## Texture Files

Put texture files in:

```txt
public/textures/
```

Load them from app code with root-relative URLs:

```js
const texture = textureLoader.load('/textures/example.jpg')
```

## The `threejs` Command Script

This repo includes a reusable scaffold script at:

```txt
scripts/threejs
```

The script creates this same starter in the current directory, installs `three`, installs `vite` locally, and leaves you ready to run `npm run dev`.

Example usage after installing the command:

```bash
mkdir my-three-project
cd my-three-project
threejs
npm run dev
```

## Install The Script On macOS Or Linux

Create a personal bin folder if you do not already have one:

```bash
mkdir -p ~/bin
```

Copy the script into it:

```bash
cp scripts/threejs ~/bin/threejs
```

Make it executable:

```bash
chmod +x ~/bin/threejs
```

Make sure `~/bin` is on your `PATH`. For zsh, add this to `~/.zshrc`:

```bash
export PATH="$HOME/bin:$PATH"
```

For bash, add the same line to `~/.bashrc` or `~/.bash_profile`.

Restart your terminal or reload your shell config, then test:

```bash
threejs --help
```

## Install The Script On Windows

The included script is a Bash script. On Windows, use it from WSL or Git Bash.

For WSL, use the macOS/Linux instructions above.

For Git Bash, a common place to put personal scripts is:

```txt
C:\Users\YOUR_NAME\bin
```

Copy `scripts/threejs` into that folder as `threejs`, then add that folder to your Windows `Path` environment variable.

In Git Bash, make it executable:

```bash
chmod +x ~/bin/threejs
```

Then test:

```bash
threejs --help
```

If you prefer native PowerShell instead of Git Bash or WSL, use this repo by cloning it directly, or port the Bash script to a `.ps1` file.

## Script Structure

The script is intentionally simple so it is easy to edit.

- Help handling: supports `threejs --help`.
- Argument guard: refuses arguments because it scaffolds the current directory.
- Dependency checks: confirms `node` and `npm` are available and prints install links if either is missing.
- Conflict checks: refuses to overwrite important files like `package.json`, `index.html`, `.gitignore`, `src/app.js`, and `src/style.css`.
- Project name: derives the package name from the current directory.
- Directory setup: creates `src` and `public/textures`.
- File templates: writes `package.json`, `.gitignore`, `index.html`, `src/app.js`, and `src/style.css`.
- Dependency install: runs `npm install three` and `npm install --save-dev vite`, with troubleshooting links if an install fails.

To customize the generated starter, edit the heredoc blocks in `scripts/threejs`. For example, change the block that starts with:

```bash
cat > src/app.js <<'JS'
```

and ends with:

```bash
JS
```

That block is the template for the generated `src/app.js` file.
