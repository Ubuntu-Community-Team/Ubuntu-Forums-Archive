---
title: "I finally got Debian to boot; few questions..."
date: 2008-01-17
forum: Debian
---

### Post by XtremeGamer99 on 2008-01-17
I've been trying for a few days to get Debian to boot into something usable. My first problem was getting it to install on an Intel RAID controller. I got through that, then my next big problem was trying to get the GUI environment to work (in this case, KDE). I didn't have the X server configured properly to my video card and display, so I used Knoppix's mkxorgconfig utility to create a xorg.config file that I then transfered to my Debian. That made it work.

I have two questions though:
mkxorgconfig it a very handy tool. I'm wanting to include it in my Debian setup, just in case I change video cards or something. It's not really on my priority list, but how can I get it to work on Debian (at the moment, it's a Knoppix-only utility).

I also want to install KDE 4.0. How would I go about doing this? I'm running a Debian testing distro with the default repositories. I tried using Synaptic Package Manager, but I don't see the new KDE (the one installed is 3.5).

I can give more info once I get home to the machine, if need be. Thanks!

---

### Post by angryfirelord on 2008-01-20
> mkxorgconfig it a very handy tool. I'm wanting to include it in my Debian setup, just in case I change video cards or something. It's not really on my priority list, but how can I get it to work on Debian (at the moment, it's a Knoppix-only utility).

You can try to find a deb package if available, but for generating xorg.conf files, I just use *dpkg-reconfigure xserver-xorg* in a terminal. Works very well.
> I also want to install KDE 4.0. How would I go about doing this? I'm running a Debian testing distro with the default repositories. I tried using Synaptic Package Manager, but I don't see the new KDE (the one installed is 3.5).
That's because it's in the experimental branch at this point and is probably broken. You can try it ***at your own risk!***
[http://pkg-kde.alioth.debian.org/experimental.html]("http://pkg-kde.alioth.debian.org/experimental.html")

---

### Post by kinematic on 2008-01-20
At this moment KDE 4 is uninstallable from experimental. How do I know....I tried :)

---

