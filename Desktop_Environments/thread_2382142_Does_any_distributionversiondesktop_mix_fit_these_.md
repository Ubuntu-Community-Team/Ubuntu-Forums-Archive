---
title: "Does any distribution/version/desktop mix fit these requirements?"
date: 2018-01-09
forum: Desktop Environments
---

### Post by Singular on 2018-01-09
Hello - 

What I am trying to do seems rather simple, but I can't seem to figure out a way to do it -

I would merely want to install a 64 bit distribution, and desktop, where I can RDPin from a Windows 10 machine, and get *true* hidpi support (ie, not hacking title bars, fonts, etc.. seperately).

All the 2D desktop environments that I have tried do not fullfill these requirements - Ubuntu 17.10 was close, but only allowed a single login w/ the native desktop environment.   Mint w/ cinnamon was also close, but I couldn't get around an issue where it crashed the desktop, and went into fallback mode.

XFCE didn't work - you could get HiDPI type performance, but opening an app like Netbeans would yield non-hidpi type results.

Any recommendations?:

Thanks!

---

### Post by TheFu on 2018-01-09
I did a little research.  Just a little, because I don't have any displays with more than 1920x1200 resolutions.  You certainly know more about this topic than I.  

There are 2 major GUI libraries used today.  Gnome and Qt.

So, here's what Gnome says about HiDPI: [https://wiki.gnome.org/HowDoI/HiDpi](https://wiki.gnome.org/HowDoI/HiDpi) 

Here's what Qt says about HiDPI: [https://doc.qt.io/qt-5/highdpi.html](https://doc.qt.io/qt-5/highdpi.html) 

Sometimes the Arch Wiki gets to the point the fastest: [https://wiki.archlinux.org/index.php/HiDPI](https://wiki.archlinux.org/index.php/HiDPI)

Both have settings and environment variables to enable or force HiDPI support on.  Have you tried those?  Of course, the RDP program used would need to support that as well.

So, perhaps this isn't a "which distro" question and it is more like which version of Qt or Gnome is being used?
On my 16.04 system running openbox, there are both Qt4 and Qt5 libraries. As for Gnome, it appears to be v3.18.

Google found this: [https://www.maketecheasier.com/best-linux-desktop-environments-for-hidpi-displays/](https://www.maketecheasier.com/best-linux-desktop-environments-for-hidpi-displays/) which I suspect you have already seen.

Whether any RDP supports HiDPI is a different question completely, altogether.  From my research, running full-screen seems the best bet, not windowed. Once you are full-screen, then I think using the Ubuntu resolution tools should work.  I like lxrandr, but there are others.

I only use RDP to talk to Windows systems.  To see Linux desktops, I'll use either X11Forwarding over ssh or x2go.  Have you tried either?  I would think that the X11 stuff would "just work" if the environment vars/settings for Qt/Gnome were set. Obviously, I don't know.

Let me try to trick my desktop into lying about the resolution for a remote X11 client application ... ok, that did not work. Sorry.

Anyway, perhaps those links will be helpful. Guess that falls into the "any recommendations" bin. ;(

---

### Post by Singular on 2018-01-09
Thanks for the recommendations :)

---

