---
title: "Radeon HD 6510G2: Radeon HD 6470M + Radeon HD 6480G (Ubuntu 19.10, Fedora 30)"
date: 2019-10-26
forum: Fedora/RedHat and derivatives
---

### Post by u666sa on 2019-10-26
What's up dudes.
I have 305E5A-S07 laptop dual booting with windows 7
AMD Dual-Core A4-3305M APU
8 Gb RAM
Radeon HD 6510G2: Radeon HD 6470M (64 &#1073;&#1080;&#1090;&#1072;) + Radeon HD 6480G  graphix

Now hear me out..

Just a week ago I've installed Ubuntu on this system. Ubuntu 19.10 if I'm not mistaken.
Well, that system had AMD configuration utility. I forgot it's name, but I could choose which program would use which graphics processor. 

Now bare with me.. I've switched to Fedora 30 (because flatpaks made Ubuntu unbearably slow to use). 

How to get that same configuration program on my Fedora 30? Plz help me out, do not send me to Fedora forums, I will not get help there. Fedora forums are full of newbs just like me, and when people that don't know much try to help you, it's not going anywhere, it's all about having a conversation that doesn't go anywhere. You can help me more than them. Plz do.

---

### Post by uRock on 2019-10-26
Moved to **Fedora/RedHat and derivatives** sub-forum.

---

### Post by oldrocker99 on 2019-10-26
The system you're using with AMD/ATI cards, which have the already built-in open-source drivers, as well as Intel's drivers.

It is *NOT* recommended to use any extra drivers; the open-source drivers were developed by ATI and the FOSS developers, and are the **best** drivers available.

In other words, relax!

---

### Post by u666sa on 2019-10-26
> **oldrocker99 said:**
> the open-source drivers were developed by ATI and the FOSS developers, and are the **best** drivers available.

Oh, I have no doubt that I have the latest drivers installed.

What I want to do is control what GPU programs use by default. I can launch a program in gnone via right click using discrete GPU, but obviously I want all programs to use discreet graphics for performance. This is what I'm after. 


```
[alex@mb2 ~]$ lspci -vnn | grep -i VGA -A 12
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] SuperSumo [Radeon HD 6480G] [1002:9649] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c625]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at a0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
--
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Radeon HD 7470M [144d:c625]
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c624]
[alex@mb2 ~]$ 

```

---

### Post by u666sa on 2019-10-27
Aga!!! SOLVED!

There is a program, called CoreCtrl, it replaces Radeon Control Center from AMD. You install it, configure profile, configure the program to run minimized on startup, and it works!

---

