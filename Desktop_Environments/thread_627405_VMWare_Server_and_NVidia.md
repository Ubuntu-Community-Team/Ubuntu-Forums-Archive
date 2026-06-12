---
title: "VMWare Server and NVidia"
date: 2007-11-30
forum: Desktop Environments
---

### Post by berzerker on 2007-11-30
I've done some searching, but didn't find much that explained my problem. Anyway, I want to use Ubuntu for development work, so I have installed it withint a VMWare server running on Windows XP. The installation runs fine and everything is up and running. However, the GUI is incredibly sluggish. Everything pops up slowly and the mouse cursor jumps from position to position when I move it around. To me it seems like the graphics drivers are not installed, at least not properly.

This is an HP laptop with a Nvidia Quadro card. Going through the xorg.config file, it is really not  identified, and it appears a generic VMWare PCI card has been recognised. I ran the xserver config again and in the section where you choose your card, it appears only as VMWare. If I choose Nvidia specifically, X won't boot up.

I know VMware creates the virtual harware layer in between, but that shouldn't mean that the card drivers should be applied wrongly should it?

---

