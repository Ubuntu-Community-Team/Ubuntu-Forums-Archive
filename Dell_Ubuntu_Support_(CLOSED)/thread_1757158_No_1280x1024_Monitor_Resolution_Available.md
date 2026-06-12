---
title: "No 1280x1024 Monitor Resolution Available"
date: 2011-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Taffman on 2011-05-13
I am a first time Linux users and I have just installed Ubuntu 10 onto my Dell Dimension 9200 and I can't get it to allow me to configure my Samsung SynchMaster 913n monitors native resolution of 1280x1024. This monitor is a Windows plug and play device so I've never needed to install the drivers that came with it when running Widows, it just works.

Is there a way to configure Ubuntu to allow the selection of 1280x1024 as I could under windows. Currently Ubuntu is only allowing me to select 1024x768. Running inxi -G shows the graphics card as:

Graphics: Card ATI RV516 [Radeon X1300/X1550 Series] X.Org 1.9.0 Res: 1024x768@60.0hz
GLX Renderer Mesa DRI R300 (RV515 7183) 20090101 x86/MMX/SSE2 TCL DRI2 GLX Version 1.5 Mesa 7.9-devel

---

### Post by mörgæs on 2011-05-13
This is not specific to Dell machines. I can not give you a precise answer, but you could begin searching in this thread:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Taffman on 2011-05-24
Panic over I finally discovered what my problem was. I had a VGA & Keyboard switch between my monitor and the two PC's that share it. It seems that Ubuntu cant get the right responses from my monitor when this device is in circuit. Removing it solved my problem.

---

### Post by Grenage on 2011-05-24
Hi Taffman.

Splitters/extenders/amps/KVMs/etc have a habit of blocking EDID data, which is what Ubuntu uses to figure out what res your screen wants.  You can get around it with a custom xorg.conf, or probably xrandr.

---

