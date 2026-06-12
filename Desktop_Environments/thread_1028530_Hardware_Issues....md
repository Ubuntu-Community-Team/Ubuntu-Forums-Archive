---
title: "Hardware Issues..."
date: 2009-01-02
forum: Desktop Environments
---

### Post by Mafuzzer on 2009-01-02
Hey Everyone

I'm new here and I need a bit of help :)

I'm running the following PC Specifications:
ASUS P5N-D Motherboard
Intel Core 2 Duo E8200
2GB RAM
nVidia 8600GT

I was wondering if my NETWORK, GRAPHICS and other drivers would work on Ubuntu. The actual type of the file is .rpm which runs on Fedora. I was wondering if the files can work on Ubuntu because I have no internet or anything.

Thanks :popcorn:

P.S - There are files which contain the "source code"...

---

### Post by stderr on 2009-01-02
Quite likely, but Ubuntu will configure itself anyway, and select drivers from Ubuntu repositories. They come in .deb format, not .rpm format. As to whether you can install the same .rpm drivers that you're using in Fedora in Ubuntu, probably not that wise... 

You can install .rpms per se, but your drivers should be largely auto-configured etc as with Fedora. I can't see you struggling with video card drivers since you're running nvidia, and I'm sure whatever network adapter's being utilised (I'm assuming integrated into the motherboard) will be detected and "just work".

However, if you do encounter problems with your driver setup, it's likely that an Internet connection of some description will *really* help. 

But whether installing rpm drivers intended for another distro will work... I can't say I'm sure. I would expect so, but I don't know. 

Anyway, it's inadvisable... no auto updates for one. 

Do you mean that you intend not to hook this box up to the 'net at all?

---

### Post by albinootje on 2009-01-02
> **Mafuzzer said:**
> 
I'm running the following PC Specifications:
ASUS P5N-D Motherboard
Intel Core 2 Duo E8200
2GB RAM
nVidia 8600GT

I was wondering if my NETWORK, GRAPHICS and other drivers would work on Ubuntu. 

For a quick idea, and DYI :
Get yourself the Ubuntu desktop installation cdrom, boot with it, and play with to find out what works and what doesn't work.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Fix is released for your video-card ->
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1075198.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1075198.html)

---

