---
title: "can't run compizFusion on kubuntu gutsy"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by dumpa on 2007-11-08
Hi,
 I followed the instructions for installing and running compiz-fusion from [https://help.ubuntu.com/community/Co...r/CompizFusion](https://help.ubuntu.com/community/Co...r/CompizFusion)
 when I run
 compiz --replace
 I get the following:
 Checking for Xgl: not present.
 Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
 Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 21
 Checking for texture_from_pixmap: present.
 Checking for non power of two support: present.
 Checking for Composite extension: present.
 Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
 Checking for nVidia: present.
 Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity
 no /usr/bin/metacity found, exiting
 Can someone help me with this?
 thanks
 Dumpa

---

### Post by FuturePilot on 2007-11-08
There's a restriction on Nvidia cards with less than 64MB of VRAM due to the black window bug. You can try to work around this with
```
SKIP_CHECKS=yes compiz
```
However you'll probably run into black windows.

---

