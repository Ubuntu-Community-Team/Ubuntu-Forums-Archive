---
title: "Compiz Fusion dies on accelerated 3D"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by mukiex on 2007-09-18
Okay, here's the setup info :

Hardware
Nvidia GeForce 8600 GTS
Core 2 Duo E4300
1GB RAM

Software
Ubuntu Gutsy (latest dist-upgrade)
KDE Desktop (problem exists in Gnome and Xfce as well)
Nvidia Driver 100.14.19 (problem existed in earlier driver)
Compiz Fusion 

If I run any OpenGL app (tested with glxgears and blender) while Compiz is up, my X server resets and I get dumped back onto kdm (happened with gdm installed as well)

My xorg.conf:
[http://pastebin.com/m5a47de5c](http://pastebin.com/m5a47de5c) (problems existed with those options under "Device" gone as well)

Any help would be greatly appreciated.

---

### Post by ricardoec on 2007-09-18
It also happens to me  since yesterday update.

I run Feisty on a nw8440 with an ATI x1600, Dual Core, 2GB mem, 256mb Video mem.

---

### Post by mukiex on 2007-09-19
The annoying part is that the only posts I can find about this issue only show up as problems with XGL. But I have an NVidia card, so I'm using THAT codepath. I think this happens each time I've installed Gutsy and done a dist-upgrade (since Alpha 1); does nobody else have this issue? No GeForce 8600's in the house?

---

### Post by mukiex on 2007-09-21
Okay, so I tried again on Gutsy Tribe 5.

My EXACT commands :

# sudo apt-get update
# sudo apt-get install linux-restricted-modules-generic

Then I went to the restricted drivers manager and installed the Nvidia driver (100.14.11 is the current latest via that method)

# sudo modprobe nvidia
# sudo depmod -a

Logged out, logged back in. Desktop effects are working, success!
Run -> gnome-terminal

# glxgears

Desktop resets back to login screen. WTF is going on here?! Am I seriously the only person dealing with this?! >_< ANGER.
Mind you, this is still on the Tribe5 LiveCD.

---

### Post by durand on 2007-09-23
I have an 8600GT, problem confirmed :( I cant run any opengl stuff by the looks of it, though glxgears doesnt crash X, I just get a black box where the gears are supposed to be....

---

