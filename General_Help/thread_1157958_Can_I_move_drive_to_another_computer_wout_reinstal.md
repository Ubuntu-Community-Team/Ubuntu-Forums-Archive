---
title: "Can I move drive to another computer w/out reinstall?"
date: 2009-05-13
forum: General Help
---

### Post by ken_23434 on 2009-05-13
I am fairly new to using Ubuntu and Linux in general.  I have "played around" with LiveCDs for about 5 or 6 years, but finally did an install about 2 months ago.  The computer I have Ubuntu installed on (v9.04) is one of my older machines.  I have another computer that is faster that I would like to use w/ Ubuntu.

Could I simply swap the hard drives between the two computers?  I do not know if Ubuntu would be able to detect the hardware differences on first boot and reload the appropriate drivers, or if it would fail to load, like a Windows installation would.

I know I can transfer all my files over after a fresh install, I was just hoping to continue with the current layout, set of installed apps, and not have a couple hours of transferring files through the network.

Thanks in advanced.

---

### Post by jerrrys on 2009-05-13
should work, but like you say...it may have trouble with the new hardware. i would take hdd out of newer computer, put it in older system. and clone the hdd, then reinstall hdd in newer computer....that way you still got a backup...

---

### Post by glotz on 2009-05-13
I moved a disk with an Ubuntu install to a completely new hardware, worked like a charm. YMMV

---

### Post by HereInOz on 2009-05-13
With Linux generally, it is happy to be plugged into any hardware for which it has the drivers, and it will work.  This is one of the great attributes of a Linux install.  If the motherboard fails, grab another machine, plug the HDD in, and you are up and running quickly.

You should be fine, unless it is using unusual hardware about which it knows nothing.

---

### Post by dandnsmith on 2009-05-13
Interesting thought. I've done it with older distros some years back, without too much impact (just to get a system running).

Most noticeable (initially) would be the graphics, which might not be usable until reconfigured (might have to rescue from the CD).
HDD is, obviously the same (but hope you aren't using LVM or RAID). RAM doesn't matter a lot. Most of the rest gets scanned for at boot, in case new hardware has been recently added.

Worth a try, I'd think

---

### Post by glotz on 2009-05-13
Note that however, a newer hdd would probably be alot faster than the old one.

---

### Post by ken_23434 on 2009-05-13
> **glotz said:**
> Note that however, a newer hdd would probably be alot faster than the old one.

All my computers are pieced together, so the "older" doesn't necessarily have a slower HDD.

I just wasn't sure if the install was as versatile as a LiveCD is for detecting hardware.  In reality, I will basically be swapping the motherboard.  I will want to move this video, DVD writer, HDD, etc...  

Thanks for the advice, everyone.  I will try and get to it later today.  I will post back with my success (or failure) so others can learn from my ... (sucess/failure to be determined)

---

### Post by LowSky on 2009-05-13
Ive done it, but here are some things to be careful about

dont install proprietary drivers , like graphics cards and such, makes it easier to run. the more basic the install the better
and make sure the drive is installed in the same order so you dont end up with GRUB errors.

---

