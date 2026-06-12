---
title: "Video problem with 7.10beta after synaptic update"
date: 2007-09-29
forum: Dell  Ubuntu Support
---

### Post by ivanlo2 on 2007-09-29
I installed the 7.10 beta on my Dell 1420n just fine, everything seemed to work on start-up including the resolution 1280x800.  I clicked on the automatic update and then restarted, next thing I know my resolution is 640x480 and I cannot change it in the Screen menu.  Anybody know what's going on?  Thanks for your help.

---

### Post by pbcartwright on 2007-09-30
do you have an NVIDIA or ATI card?? those need special drivers. On my laptop I installed 915resolution to get mine working, but it really depends on your graphics card..
look at /etc/X11/xorg.conf it is a text file with your configuration settings in it.
mine says Driver "nvidia" for the video card.

---

