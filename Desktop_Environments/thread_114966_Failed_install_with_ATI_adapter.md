---
title: "Failed install with ATI adapter"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Gritz on 2006-01-09
I installed Ubuntu 5.10 from a cdrom and it has a problem with my graphics.  The message I get is this:

  "X-Server in now disabled. Restart GDM when it is correctly figured."

I am a newbie with linux, but I think it does not know how to load drivers for my video card, which is an ATI Radeon Xpress 200 Crossfire (integrated on the MSI motherboard).  So I'm guessing that I need both the drivers, and the instructions on how to get them loaded from a command prompt?

Ubuntu does not work with the "Live CD" either, which I think has the same problem?

Any help appreciated. :confused: 

Gritz

---

### Post by Zimmer on 2006-01-10
Hi,
See if these locations help
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
and 
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
Particularly the Troubleshooting section at the bottom of the page which gives instructions on installing xorg drivers with x stopped, and how to restart x...
The bad news is I don't see your particular graphics card here..
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
and the advice here
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
is a bit behind PCI Express cards
Realisticly, the omens are not good for a quick (if any) fix..
But loading the fglrx drivers and configuring is probably worth a try.
or try contacting the guys at this thread ..as they seem to have the same graphics..
[http://ubuntuforums.org/showthread.php?t=106515](http://ubuntuforums.org/showthread.php?t=106515)
regards
regards

---

