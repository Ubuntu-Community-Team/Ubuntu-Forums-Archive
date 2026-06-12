---
title: "Having a problem starting UT2004"
date: 2006-08-25
forum: Gaming &amp; Leisure
---

### Post by Odinist on 2006-08-25
I install UT last night, but when I tried to start it, it would bring up the initial starting screen, and then close. I tried opening it in a terminal, and this is what I got...

root@ubuntu:~# ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault] 
Aborting.


Crash information will be saved to your logfile.
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  79 (X_FreeColormap)
  Resource id in failed request:  0x260000c 
  Serial number of failed request:  114
  Current serial number in output stream:  116


Any ideas?

---

### Post by Relic2K on 2006-08-25
What is the make and model of your video card, it would help if we knew what kind of hardware you have :)

     Your either not running 3D Acceleration or GLX is not enabled. Make sure you Read the directions for your specific Video Card Driver, or search these forums for how to install the drivers properly.

---

### Post by Odinist on 2006-08-25
Good question. =) I'm at work right now, so I can't look. It was a loner card from a friend, pretty sure it's ATI chipset, 32 Vram, I think... I'll post something more conclusive when I get home.

---

### Post by Relic2K on 2006-08-25
Just do a search of the forums for ATI then. There is an ATI How to in the forums. I have an NVidia card myself so I will not be able to provide anymore assistance. I have an ATI Mobile chipset on my laptop, but I don't game using my laptop.

---

