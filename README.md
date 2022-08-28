# egui_example

A simple example how to use egui-wgpu-backend with egui-winit-platform to create a GUI
application using egui. This example shows how to integrate egui into
your own engine.

This version has been updated to use egui 0.19, winit 0.27, and wgpu
0.13. It should also work on WASM targets once [this
PR](https://github.com/gfx-rs/wgpu/pull/2954) has been merged into
wgpu. To make WASM work, all feature flags for the `egui-winit` crate
have been disabled. None seem to have been required for the example,
and clipboard isn't supported for web. You may wish to re-enable some
features for your own projects.

Note that the package structure is a bit different nowadays, so the
`egui_wgpu_backend` and `egui_winit_platform` packages below are for
reference only. See this example and the current [egui integration
docs](https://docs.rs/egui/latest/egui/#integrating-with-egui).

 - [egui](https://github.com/emilk/egui)
 - [egui_wgpu_backend](https://github.com/hasenbanck/egui_wgpu_backend)
 - [egui_winit_platform](https://github.com/hasenbanck/egui_winit_platform)

## Compiling to WASM

The easiest way is probably to use
[cargo-webassembly](https://wasm.js.org/crates/cargo-webassembly/). You'll
need to add `--cfg=web_sys_unstable_apis` to your `RUSTFLAGS`
environment variable, otherwise you'll be missing a bunch of
GPU-related stuff from web_sys.

Note that until [this PR](https://github.com/gfx-rs/wgpu/pull/2954) is
merged, attempting to compile to WASM will give an error about
`Depth24unormStencil8` missing from the `GpuTextureFormat` enum,
because it does not exist on WebGPU.

## License
This example is public domain.
