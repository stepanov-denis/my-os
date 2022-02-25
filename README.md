# My OS
Simple OS on Rust
## Prerequisites
* Install Rust for Linux or macOS
```
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```
For Windows, visit [this page](https://www.rust-lang.org/tools/install)
* Install nightly Rust
```
$ rustup toolchain install nightly
```
* Setup [QEMU](https://www.qemu.org/download/)
## Initial setup
* Building
```
$ git clone git@github.com:stepanov-denis/my-os.git
$ cd my-os
$ rustup override set nightly
$ cargo build
$ cargo install bootimage
$ rustup component add llvm-tools-preview
$ cargo bootimage
```
* You can run the disk image in QEMU through:
```
$ cargo run
```
* Working on bare metal
```
$ sudo dd if=target/x86_64-my_os/debug/bootimage-my-os.bin of=/dev/sda1 && sync
```
Where sdX - the device name of your USB stick
* For run tests
```
$ cargo test
```
* For run tests that should panic
```
$ cargo test --test should_panic
```