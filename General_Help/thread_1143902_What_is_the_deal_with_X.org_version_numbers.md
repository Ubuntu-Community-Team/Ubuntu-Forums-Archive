---
title: "What is the deal with X.org version numbers?"
date: 2009-04-30
forum: General Help
---

### Post by delcypher on 2009-04-30
Hi I'm trying to decide whether or not to install Ubuntu 9.04 (uses X.org X server version 1.6.?) depending on whether my graphics card will work properly (2D & 3D) (ATI RADEON HD4830 - R7xx - chipset I think). It works fine on 8.10 using the proprietary ATI driver.

What is really confusing me is the X.org version numbers, they make no sense when comparing them to what's on the ATI site. 

If I use the proprietary [ATI driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English") then apparently the most recent X.org version supported is 7.4.

Okay so I decided to run 
```
Xorg -version
```

Which gives
```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux dan-desktop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
```

Which tells me the version of X.Org X server I'm running is 1.5.2. That's fine but how does that relate to ATI saying I need X.org 6.7 or greater!!


On another note, I'm not sure about the open-source driver. I've no idea where to get that from and if it supports my chipset.

Thanks.

---

### Post by LowSky on 2009-04-30
Xorg newest release 7.5 uses xorg-server 1.6/1.7 (I know its confusing), released Decemebr 2008

your fine, it will work in 9.04

[http://www.x.org/wiki/Releases/7.5](http://www.x.org/wiki/Releases/7.5)

---

### Post by delcypher on 2009-04-30
Ok that sort of clears it up. I really can't see the point of the two different version numbers.

7.5 - Is that the release number? 1.6.x - Is that the X.Org server version. Is X.Org server only one small part of X11R7.5 so it gets its own version number?

So if Ubuntu 9.04 uses X.org X server 1.6.? that translates (ATI's way of saying it) to X.Org 7.5, that means the proprietary ATI driver will not work (only supports upto 7.4) which means I WON'T be fine.

Any info on the opensource ATI driver?

---

### Post by Nepherte on 2009-04-30
As far as I can tell, Ubuntu 9.04 uses xorg 7.4: [http://packages.ubuntu.com/jaunty/xorg](http://packages.ubuntu.com/jaunty/xorg). Xorg 7.5 is still in development.

---

### Post by delcypher on 2009-05-01
Hmmm I'm not sure (xorg (1:7.4~5ubuntu18) - I'm not sure how the version number works for ubuntu packages). I got my information from [https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview#X.Org%20server%201.6]("https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview#X.Org%20server%201.6")

This claims Ubuntu uses X-server 1.6 which I believe is part of X.Org [7.5]("http://www.x.org/wiki/Releases/7.5"). If you look at the X-server version on the page it lists 1.6.

---

### Post by Nepherte on 2009-05-01
Well, it's both yes and no.

Xorg is a bundle of many X related things such as X server. The version number of X Server doesn't relate in any way to Xorg apart from the sole fact that *a* version of X server will be included. It's the same as saying Ubuntu 9.04 includes gnome 2.26.1: the gnome version has on its own nothing to do with Ubuntu.

The page you refer to actually demonstrates what I'm saying:
 First of all:
> X.Org 7.5 development is currently underway.
so there's no 7.5 as of yet.

Second:
> Features added/enhanced:xorg-server 1.6.0 or 1.7.0.
clearly demonstrates that there hasn't been decided yet what version of xorg server will be included.

If you look a little further on the jaunty page you link to, it will say that they use X.org 7.4:
> he latest X.Org server, version 1.6, is available in Jaunty. The latest Mesa 3D DRI, version 7.4, is also available. A number of video cards have been transitioned to free drivers as part of these updates.

---

