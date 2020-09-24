# wasm-studio-utils

## Overview

This package is [**WebAssemblyStudio**](https://webassembly-studio.kamenokosoft.com) subset that is intended to work on local environment.

Original Project: <https://github.com/yurydelendik/wasm-studio-utils>

## Supprorted Features

- Read/Write file contents in Project
- Queue compilation task to online compiler service, and download built wasm file.

## Supported Compile Target

- WebAssembly

## Available Languages

- C/C++ (emscripten backend)
- Rust

## Build task sample

```js
const { Service, project } = require("wasm-studio-utils");

(async function build() {
    const data = await Service.compileFiles([
        project.getFile("src/main.cpp"),
        ], "cpp", "wasm", "-O2");
    const outWasm = project.newFile("out/main.wasm", "wasm", true);
    outWasm.setData(data["a.wasm"]);
    const outJS = project.newFile("out/main.js", "javascript", true);
    outJS.setData(data["wasm_bindgen.js"]);
})();
```
