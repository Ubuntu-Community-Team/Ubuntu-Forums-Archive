---
title: "dispite following the guides, vega strike wont work"
date: 2009-07-20
forum: Gaming &amp; Leisure
---

### Post by PsYcHoTiC_MaDmAn on 2009-07-20
tried installing vega strike for the 3-4 time 

have used synaptic package manager, add remove apps, direct downloads and through terminal.

it is installed, and shows up in the menu

however nothing happens when I try and launch it

having followed the guide on this thread [Ubuntu 64-bit Gaming Guides](http://ubuntuforums.org/showthread.php?t=662770)[Vega Strike Guide](http://gwos.org/doku.php/guides:64bit:vega_strike)

it downloads the libraries with no issue. 

however CG Program Mamager is no longer at the link provided and searching the getdeb.net I cant find a newer version

so therefore the command to get it to work with ogre is of little effect

ogre installs without much issue, except gives this at the end of the commands listed 
> checking for ZZIPLIB_LIBS... 
configure: error: Package requirements (zziplib) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the ZZIPLIB_CFLAGS and ZZIPLIB_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
ben@ben-desktop1:~/Desktop/ogrenew$ make
make: *** No targets specified and no makefile found. Stop.
ben@ben-desktop1:~/Desktop/ogrenew$ sudo make install
[sudo] password for ben: 
make: *** No rule to make target `install'. Stop.


I've tried installing it on another pc and gotten nowhere either (that was also an x64 machine)

spec wise my PC should be up for it  AMD Phenom 2 x4 940 (4*3GHz) 8GB DDR2 800, nVidia GeForce 8200TC 1GB Direct X10 Graphics (admittedly integrated, but better than a lot of previous AGP cards.(especially given whats down as a minimum requirement for video cards for vega strike))

---

### Post by Grishka on 2009-07-20
I'm afraid Ogre didn't install correctly for you. it didn't even make correctly. [apt://libzzip-dev](apt://libzzip-dev), then configure, make and make install again.

---

