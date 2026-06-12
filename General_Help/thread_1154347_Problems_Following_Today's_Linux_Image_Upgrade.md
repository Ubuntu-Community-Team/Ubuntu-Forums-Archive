---
title: "Problems Following Today's Linux Image Upgrade"
date: 2009-05-09
forum: General Help
---

### Post by Billsey on 2009-05-09
I appreciate all the work that the Ubuntu team does, but I suddenly have problems after today's upgrades.

8.04.2 Hardy Heron (LTS)
T2482 EMachine
AMD Athlon XP 2400+
1.25 GB RAM

I just upgraded with today's new Linux image (along with some other stuff; there were 15 packages involved in the upgrade), and all of a sudden, my USB has gone loopy. I had to connect my keyboard and mouse via USB-to-PS2 adapters to make them usable (mouse jumping around screen; keypresses being missed), and mounting USB drives takes a ***seriously*** long time, and even then transfer speeds are like USB 1.1 instead of 2.0 (if even that fast; it might be more like floppy speeds). It looks as if the USB controller/software is busy looping so badly as to make it almost unusable.

Also, I now have to hit F1 to finish the boot every time I boot up. Something bad has happened with this upgrade (perhaps involving the BIOS?). Hopefully, it can be quickly corrected.

---

### Post by mikezila on 2009-05-09
What happens if you use an older kernel?  You should still have at least one in the boot loader menu.

Does that fix it?

---

### Post by Billsey on 2009-05-09
I tried going back to the previous kernel, but got the same symptoms, which doesn't make sense to me, since the symptoms only showed up after rebooting following the kernel upgrade. It's almost like something went wonky in the BIOS, but I can't figure out what that would be.

---

### Post by Tipped OuT on 2009-05-09
The bios has nothing to do with this, unless you where playing with it before you started noticing these problems occur.

I think it was just a bad upgrade (happens a lot). Back up your stuff, and do a fresh install, that's what I suggest.

---

### Post by mikezila on 2009-05-09
If changing the kernel version causes no change in the symptoms, then it likely isn't the cause.

What were the other packages upgraded?

---

### Post by -kg- on 2009-05-09
> What were the other packages upgraded?

Always assume that a person doesn't have as much experience as you, and tell him how to check that.  Even I don't know that, and would appreciate finding out.

Luckily, on the computer that has Hardy still installed, I didn't have any problem with the update.

---

### Post by mikezila on 2009-05-09
Sorry.  Got ahead of myself.  You can find out what packages have been installed/upgraded/removed by using the "System Log Viewer".  It's in System->Administration.  The log we'll be most interested in is called "dpkg.log", it'll be in the list at the left, somewhere north of the middle.

If you scroll all the way down (logs are always appended, so new stuff is always at the bottom) you should see the last packages that were interacted with.  You can use the dates on the left to get a frame of reference.

Post what you see for the day you did the upgrade till now.

You might also be able to skip all of this by checking the "syslog", near the bottom of the list.  Scroll around in there and see if you spot any scary looking error messages relating to the problems you're having.

Also, as an aside, if you're havin' trouble, poking around in the logs is a good way to see error messages that might be happening behind your back.  If something goes screwy, check "syslog" and any other ones that seem relevant.

---

### Post by Billsey on 2009-05-16
Sorry for the delay, folks. Things have been pretty crazy around here. Turns out it had nothing to do with software. It's something with the power supply, or the motherboard, or the board that has the lighted power switch. The computer now refuses to even post—which makes it definitely hardware. The hard drive is fine. All data has been recovered, by putting the drive into an external USB enclosure, then mounting that up on my laptop. Now to get that computer repaired.

---

### Post by Billsey on 2009-05-25
**UPDATE:**
I was given a new**ER** motherboard with a 1.8GHz P4 and bought a 500 watt power supply to run it. I've basically combined several different systems (the contents of the "home" directory from the Athlon; the case and drives from my old Celeron; and the motherboard that was given me). I put them all together and started up just to see how confused the system would be.

Get this: so far everything seems to work great!!!

Someone please explain to me again, how Windows is so much better than Linux. :D

---

