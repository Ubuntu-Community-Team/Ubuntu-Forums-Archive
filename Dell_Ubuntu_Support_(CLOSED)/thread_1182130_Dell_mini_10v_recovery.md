---
title: "Dell mini 10v recovery"
date: 2009-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OldJohnB on 2009-06-08
I am planning to buy a mini 10v with Ubuntu OS and I would like to know how Ubuntu can be restored if damaged or removed.  For example is the "Dell Version" of Ubuntu on a hidden HD partition or on a CD?  Also how does the Dell Ubuntu 8.04 differ from the regular Ubuntu 8.04?  I note that Dell has added some enhanced wireless network software interface - is this just added after a regular Ubuntu installation or is it an integral part that cannot be separated?  I have also seen mentioned that the Dell Ubuntu updates are from a Dell repository, is this correct?

 

OldJohnB

---

### Post by Brandon Williams on 2009-06-09
Dell will send you a DVD with Ubuntu on it. Unless you actually have a DVD drive for the mini, this won't be too useful as a restore option.

I recommend that you get yourself a USB thumb drive and install a live CD version of Ubuntu to it. This will allow you to boot the machine for troubleshooting if something goes wrong. Once you have the USB set up, boot off of the usb stick and use dd to make a complete copy of the initial installation (before you do anything to it). That way, if you manage to make the system unusable through experimentation, you can restore the original install in very little time. Even if you have a big hard drive, it's possible to compress the disk image to allow it to fit in a relatively small file.

I ordered a mini 10v myself just a few days ago and should receive it next week some time, I think. I'm currently running a mini 9. There was very little installed on it that was not stock Ubuntu. It comes with multimedia codecs preinstalled, flash, and acroread preinstalled, as well as a couple of dell custom apps, but nothing important that you can't get working on a stock Ubuntu install.

The big difference is that it's installed with lpia (low power intel architecture) builds of all the software, which means that most third-party software will be unavailable without some annoying repackaging of i386 architecture packages. There have been some complaints about the timeliness (or lack thereof) of security updates to the Dell repositories.

---

### Post by snowpine on 2009-06-09
The Dellbuntu 8.04 recovery image is easy to find on the web. [http://www.mydellmini.com/forum/ubuntu-netbook-remix/271-dell-mini-9-ubuntu-restore-iso-image.html](http://www.mydellmini.com/forum/ubuntu-netbook-remix/271-dell-mini-9-ubuntu-restore-iso-image.html)

Many Dell Mini users have replaced Dellbuntu 8.04 with a different OS. Ubuntu 9.04 (either the regular or netbook remix version) seems to be the most popular. Here is some info: [http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html](http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html) I personally am dual booting Arch and Slitaz on my Mini 9, though I can't really recommend either if it's your first Linux experience.

---

### Post by karamu on 2009-07-29
From what I gather the networking working capabilities for the Dellbuntu 8.04 is a backport from 8.10. I just got my 10v the other day and I can confirm that it uses Dell's repositories. I am not too happy about the Dell version and will most likely install Jaunty sometime soon.

---

### Post by ClarkBennett on 2010-01-12
Thanks, snowpine, for the Dellbuntu 8.04 link.  However the download page states "This iso will ONLY work on a Dell Mini 9 netbook."   Will it also work on the Dell Mini 10v with a 16GB SSD?  I have just order mine and want to be sure I can restore it because I am almost certain to mess it up.

---

### Post by snowpine on 2010-01-12
> **ClarkBennett said:**
> Thanks, snowpine, for the Dellbuntu 8.04 link.  However the download page states "This iso will ONLY work on a Dell Mini 9 netbook."   Will it also work on the Dell Mini 10v with a 16GB SSD?  I have just order mine and want to be sure I can restore it because I am almost certain to mess it up.

I cannot say with 100% certainty, however my understanding is that the Mini 9 and Mini 10v are 99.9% the same hardware. Dell could tell you for sure...

---

