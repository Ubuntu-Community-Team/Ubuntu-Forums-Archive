---
title: "Inspiron 530: 10.04 live CD hangs booting from USB"
date: 2010-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gbrainin on 2010-05-08
I am trying to figure out what is different about the 10.04 live CD from prior releases that prevents the CD from working properly, but only when run as a USB CD.  To explain:

I have an Inspiron 530 (came with 7.10, now running 10.04) and I recently purchased a SanDisk USB drive.  The drive came with a Windows-only system called U3, which does its thing by pretending to the system that it is both a regular USB drive and a USB CD-ROM.

Following the instructions [here (http://randommusingsofarealgeek.blogspot.com/2009/12/u3-howto-1.html)]("http://randommusingsofarealgeek.blogspot.com/2009/12/u3-howto-1.html"), I used the u3-tools package to reconfigure it so that the Ubuntu live CD was the fake CD, instead of the original software.  The idea is that the system should be able to boot off the USB CD, and it works fine when I tried an older version (8.04), but not so much with 10.04.

With the 10.04 live CD ISO loaded on the USB drive, it does boot, and it will get to the live CD menu.  However, when it tries to load the operating system, it hangs on a blank screen with a cursor blinking.

The same ISO burned to a CD boots up fine.  When I used the startup disk creator with the same ISO, it worked (on another computer; the 530 doesn't like to boot from removable USB devices).  So it must be some combination of the USB-CD drive and something different about 10.04.

Anyone know what it might be getting stuck on?  It would be great if it were some configuration file I could fix, but I'm a bit stuck and hoping someone has some ideas to help out.

---

### Post by linuxlist on 2010-05-29
I think you should try after removing U3 and using Startup Disk Creator on Ubuntu System-Administration menu.

casper might not be approaching the U3 system like Windows or older versions should...

Regular USB created like mentioned works like a charm.

---

### Post by gbrainin on 2010-05-29
The point was not just to get the USB stick to boot on my computer, but to get it to boot from the fake CD portion of the USB stick.  Why?  Because the fake CD boot (but not the regular bootable USB) works on my work computer, and I'm looking for a single setup that works on both.

I did come up with a workaround.  By installing a small linux distribution (PLoP) on the fake CD and Ubuntu on the main portion, I can boot from the other distribution then select Ubuntu from the boot menu.  It would still be interesting to know what changed between the different versions of Ubuntu, especially if it's something that could easily be worked around.

---

