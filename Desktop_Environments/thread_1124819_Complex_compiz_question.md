---
title: "Complex compiz question"
date: 2009-04-13
forum: Desktop Environments
---

### Post by mrq201 on 2009-04-13
Ok here is the deal.  When i first installed ubuntu 8.10, I had issues after i typed in the user name and password.  After i typed in the user name and password, all i received was the default ubuntu wallpaper and the mouse cursor.  

I did some searching and found a fix for it. 
The fix i used were these commands

sudo apt-get remove compiz
sudo apt-get remove compiz-core

So after i used this fix, i was able to boot up into ubuntu.  Everything was fine and dandy until i started to play around with it and read forums.  Oh yeah, i am a big newbie to linux.

So i tried the compiz command and i got this

Checking for Xgl: not present
Detected PCI ID for VGA
Checking for texture from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present
Checking for non power of two support: present
Checking for Composite extension: present.
Comparing resolution (1600x1050) to maximum 3D textue size (2048): Passed
Checking for Software Rasterizer:  Not present.
Checking for nVidia: Not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz: 422 /usrs/bin/compiz.real: not found

If anyone can assist me with anything, I would very much appreciate it.

---

