---
title: "Unreal Tournament 99 - install fails on 14.04"
date: 2014-07-28
forum: Gaming &amp; Leisure
---

### Post by sorceror171 on 2014-07-28
I've tried following the instructions here: [https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

However, it does not result in a playable installation. This is on a machine with a Gigabyte g31m-es2l motherboard, Celeron CPU, 2GB RAM. It uses the Intel GMA 3100 video chipset, which should be more than adequate for a game from the previous century. First I tried Xubuntu 14.04 AMD64, managed to install the required 32-bit libraries, but... it segfaulted the instant it tried to initialize OpenGL. (Same problem as here: [http://ubuntuforums.org/showthread.php?t=1937484](http://ubuntuforums.org/showthread.php?t=1937484) which was never resolved.)

So, I wiped and reinstalled Xubuntu 14.04 i386. Two libraries were necessary, (libglib1.2 and libgtk1.2, fetched per these instructions: [http://www.ubuntugeek.com/how-to-install-xmms-on-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-xmms-on-ubuntu-10-04-lucid.html)), and glxinfo and glxgears both show an operational OpenGL subsystem, but still no dice.

What's *really* strange is a I have a Xubuntu 14.04 system on much different hardware (Core i7, 16GB RAM, Geforce 560 Ti) and it *does* run UT99 with no problems. In fact, I tried copying that install directory over from the old system to the new one, and that suffers the same problem as a fresh install.

I got so annoyed I even swapped out the hard drive and installed Windows XP on that machine, after digging out all the correct drivers and such. UT99 runs fine on that machine with the OpenGL renderer; if there's some element of OpenGL that isn't supported, it's a Linux-specific issue, the hardware itself is perfectly capable. Indeed, I may have tracked down the problem: [https://bugs.freedesktop.org/show_bug.cgi?id=37637](https://bugs.freedesktop.org/show_bug.cgi?id=37637)

Does anyone have UT99 running on a recent Ubuntu with a non-Nvidia video card?

---

### Post by R33D3M33R on 2014-07-28
I'm running UT99 on Kubuntu 14.04 and AMD HD7750 (fglrx installed) on a 64-bit system. I always use the wiki instructions to install (btw. I did also do some editing of this page). It definitely seems like a driver problem in your case.

---

