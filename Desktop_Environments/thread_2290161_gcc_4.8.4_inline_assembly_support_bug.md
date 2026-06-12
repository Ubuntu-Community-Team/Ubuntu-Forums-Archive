---
title: "gcc 4.8.4 inline assembly support bug?"
date: 2015-08-10
forum: Desktop Environments
---

### Post by gary-yin on 2015-08-10
ubuntu version: Ubuntu 14.04.2 amd64
Environment: Virtualbox 5.0, Host OS Win8.1 x64

related source code:
asm volatile ("vmovapd ymm0, [rsp]" : : : "ymm0");

compile command: gcc -m64 -masm=intel -o man main.c

error message:
error: unknown register name 'ymm0' in 'asm'
asm volatile ("vmovapd ymm0, [rsp]" : : : "ymm0");

By the way, if I use latest TDM-GCC(gcc 5.1.0) windows version to compile the same source, it's OK!

---

