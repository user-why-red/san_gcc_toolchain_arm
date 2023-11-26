###                 SAN-GCC

This is a GCC compiler toolchain that is built for kernel development. Builds are always made from the latest GCC(stable releases).

### SUPPORTED HOST MACHINE ARCHITECTURES:
• Arm(64bit/32bit).

### SUPPORTED TARGET ARCHITECTURES:
• Arm(64bit/32bit).

• x86_64.

This toolchain targets the AArch32, AArch64, and x86_64 architectures. It is built with LTO and O3 optimizations to reduce compile times as much as possible. Note that this toolchain is not suitable for anything other than bare-metal development; it has not been built with support for any libc or userspace development in mind.

binutils is also included for convenience. SAN-GCC uses binutils source from the HEAD of the latest release branch, which allows us to have more upto date binutils compared to latest stable release as well as avoiding instability or breakage compared to bleeding edge binutils.

### COMPILING LINUX KERNEL WITH SAN-GCC:

Make sure you have this toolchain in your PATH:

[+] ***export PATH="$HOME/toolchains/san-gcc/bin:$PATH"***

For an AArch64 cross-compilation setup, you must set the following variables. Some of them can be environment variables, but some must be passed directly to make as a command-line argument. It is recommended to pass all of them as make arguments to avoid confusing errors:

[+] ***ARCH=arm64***

[+] ***CC=aarch64-linux-gcc (must be passed directly to make)***

[+] ***CROSS_COMPILE=aarch64-linux-***

If your kernel has a 32-bit vDSO:

[+] ***CROSS_COMPILE_ARM32=arm-linux-gnueabi-***

Note: Android kernels 4.19 and newer use the upstream variable CROSS_COMPILE_COMPAT. When building these kernels, replace CROSS_COMPILE_ARM32 in your commands and scripts with CROSS_COMPILE_COMPAT.