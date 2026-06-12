---
title: "Screen Resolution: 1680x1050 easily supported?"
date: 2007-01-29
forum: Desktop Environments
---

### Post by monocongo on 2007-01-29
I have just started running Ubuntu on my machine using the Live CD for Ubuntu 6.1.0.  It looks good and I hope to be able to replace Windows XP with Ubuntu in the next few days when I feel ready to take the real plunge.  The first thing that I've noticed however is that the screen resolution that I normally use with my widescreen monitor, 1680x1050, doesn't appear to be supported by default (I can only choose 800x600 or 640x480).  Is this something I would be able to easily adjust once I fully install Ubuntu onto my system, or are there other steps I'd need to perform in order to be able to fully realize the potential of my monitor?  I'm reasonably adept at the Unix command line so I'm not afraid to do a bit of configuration in order to get this to work, but on the other hand I don't want something like this, which I get by default with Windows, to be much of a time drain.

Thanks in advance for any ideas or suggestions.


--James

---

### Post by taurus on 2007-01-29
Yes, you can run with that resolution.  You first need to install a driver for your graphic card and what is it anyway?

---

### Post by Ramses de Norre on 2007-01-29
The live cd is made to run fast and without tweaking on as many systems as possible so such things as high resolution screens are often not supported. 
In the installed version it will be possible though. As already mentioned it's as easy as installing the right driver and picking the resolution from a menu (in the worst case editing one line in a config file).

---

### Post by monocongo on 2007-02-02
Thanks for the information.

My video card is an ATI Radeon Xpress 200.  

I'm a bit discouraged by the info I've found which discusses this video card using Linux:

[http://www.linuxforums.org/forum/ubuntu-help/64489-ati-radeon-xpress-200-cant-change-screen-resolution.html](http://www.linuxforums.org/forum/ubuntu-help/64489-ati-radeon-xpress-200-cant-change-screen-resolution.html)
[http://www.fys.uio.no/~henger/htpc/radeon_xpress_200.html](http://www.fys.uio.no/~henger/htpc/radeon_xpress_200.html)
[http://lists.freedesktop.org/archives/xorg/2005-November/011224.html](http://lists.freedesktop.org/archives/xorg/2005-November/011224.html)

Two questions come to mind (sorry they're a bit off topic):
1) How to find the latest/greatest instructions for this sort of configuration, apart from asking other users on the various Linux forums or buying a support contract?  It seems that there's lots of information out there, but pulling the signal out of the noise looks like it may take quite a bit of effort. (I know, I know -- what do I expect for free?)
2) Is there a central repository for drivers, etc. which makes finding the latest versions easy?


--James

---

### Post by monocongo on 2007-02-14
I finally took the plunge and installed Ubuntu.  The first thing I did was to install the driver for my video card, using the instructions found here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

In summary:
    [LIST=1]
[*]sudo apt-get update
[*]sudo apt-get install linux-restricted-modules-$(uname -r)
[*]sudo apt-get install xorg-driver-fglrx
[*]sudo aticonfig --initial
[/LIST]

When I rebooted everything looked good, I didn't even have to set the resolution myself, it was already set to 1680x1050.


--James

---

### Post by brakit on 2007-03-19
Thanks for the information.  This worked beautifully for me.  I had been trying to figure this out for about two days.

---

