---
title: "Mouse cursor keep spinning opening 2nd file"
date: 2019-05-10
forum: Desktop Environments
---

### Post by corradoventu on 2019-05-10
Ubuntu 19.10: double click on a text document to open it: ok. while the 1st document is open I click on a 2nd document: the document opens but the mouse cursor keep spinning for about 15 seconds.
The problem does not disturb because the 2nd document is immediately available and i can type on it, i'm just curious about the strange behaviour of the cursor.
Here the screencast: [https://drive.google.com/file/d/137y79khk6MvPgqCetpmqcMBfwRb46PTz/view](https://drive.google.com/file/d/137y79khk6MvPgqCetpmqcMBfwRb46PTz/view) 
Nautilus is 1:3.32.0-0ubuntu2
```
corrado@corrado-p7-ee-0507:~$ inxi -SCGx
System:
  Host: corrado-p7-ee-0507 Kernel: 5.0.0-13-generic x86_64 bits: 64 
  compiler: gcc v: 8.3.0 Desktop: Gnome 3.32.1 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31296 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.4 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) 
  v: 4.5 Mesa 19.0.2 direct render: Yes 
corrado@corrado-p7-ee-0507:~$ 

```
Problem occurs also in Ubuntu 19.04 - same nautilus version
but does NOT occur in Ubuntu  18.04.2 LTS with nautilus 1:3.26.4-0~ubuntu18.04.4

---

