---
title: "Do I need ATI drivers / hardware acceleration to get Compiz to work?"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by blimbo on 2007-10-29
I've got an ATI Radeon 8500 but am having big problems with the ATI driver/kernel module; unfortunately the last driver to support this was 8.28.8-1 and I've tried for about a week now to compile the module using this version and my current kernel source (2.6.22-14-generic) but it's having none of it.

glxgears is quite good i think:

tim@ubuntu:~$ glxgears 
6390 frames in 5.1 seconds = 1257.830 FPS
6480 frames in 5.0 seconds = 1290.073 FPS
..
23354 frames in 5.0 seconds = 4655.437 FPS
23241 frames in 5.0 seconds = 4636.711 FPS
22713 frames in 5.0 seconds = 4533.124 FPS
22111 frames in 5.0 seconds = 4417.115 FPS

using the Radeon driver that came with Ubunut (7.10). Despite this I can't get Compiz running: 

tim@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:514c (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

I've sort of got it to run but I lose my borders and don't get any effects, but now it reverts straight back to metacity. I've tried installing Xgl-server but the system slows down and is pretty unusable (and Compiz still doesn't work).

So is this due to me not using the ATI driver or is there another issue? I'm considering a cheap Nvidia card from ebay..

---

### Post by infamous16 on 2007-10-29
I installed my ati drivers and compiz no longer worked, than I disabled them and it did work...and at my friends house with or without the driver it didnt work.

---

