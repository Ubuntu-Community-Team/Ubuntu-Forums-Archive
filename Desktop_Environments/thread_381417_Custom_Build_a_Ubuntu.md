---
title: "Custom Build a Ubuntu"
date: 2007-03-10
forum: Desktop Environments
---

### Post by in_flu_ence on 2007-03-10
Is there a way to custom build ubuntu in the sense that I will have the least amount of stuff necessary to boot up linux and the bare minimum of gnome to run the X server?

I am hoping that I can get a running system with 700mb. I mean a system with gnome but with no application (e.g. openoffice, no media player, no game etc.)

Any chance?

Thanks

---

### Post by rsambuca on 2007-03-10
Probably the easiest way is to do a server install, and then ```
sudo aptitude update
sudo aptitude install gnome-core
```

---

### Post by in_flu_ence on 2007-03-10
There doesn't seem to have gnome-core in the dapper default list

I m using the dapper server list 'cause I want to get a custom build ubuntu for LTS.

---

### Post by K.Mandla on 2007-03-10
You can start with a server and get it under 500Mb. Adding something like Openbox or Fluxbox will push it to around 700Mb, I believe.

The problem is that any graphical environment pulls in xorg, which can be quite hefty once it's unpacked. If you're sneaky and you rip out things you don't need (like the video drivers that you don't use :???: ), you might be able to trim it down from there.

---

### Post by in_flu_ence on 2007-03-11
If I am to use xubuntu-desktop package and I am going to install the ubuntu OS in a pen drive so that i can use in a few places, do you think i will just need one set of video driver, 1 network driver (I don't even think I need even the madwifi and etc drivers? right?) 

I really hope to squeeze into a pen drive rather than a portable harddisk. so i can just bring it easily to do presentation, do some work etc.

Thanks

---

### Post by jem7v on 2007-03-11
Well, you'd probably need video drivers for every kind of video card used in the computers you plug it into, so you might need a few.  Might be the same issue with your network driver, but I'm not really sure about that...

If you want to have a pen-drive bootable Linux installation, you might want to check out [DSL]("http://www.damnsmalllinux.org/") instead of Ubuntu (or its heftier cousin, [DSL-N]("http://www.damnsmalllinux.org/dsl-n/")), as it's very well suited for pendrives.

---

