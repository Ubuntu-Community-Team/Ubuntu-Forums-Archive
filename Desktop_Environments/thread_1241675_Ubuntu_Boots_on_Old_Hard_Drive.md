---
title: "Ubuntu Boots on Old Hard Drive"
date: 2009-08-16
forum: Desktop Environments
---

### Post by ttoolin on 2009-08-16
Hi folks-

I have a hard drive configuration problem:

I have ubuntu installed on an old Dell box (P3, circa 1999), which came with a 6 gig hard drive.  When it became obvious that within a fairly short period of use, that I was going to fill it up, I bought a 20 gig hard drive, and after much diving into the docs, managed to format it, transfer the data from the 6 gig to the 20 gig, and had the partition manager make the 20 gig hard drive the boot drive.

Success.  I then pulled the plug on the 6 gig drive, keeping it intact, in case the new drive (which I bought used) crashed.

Now I'm ready to use the 6 gig drive as a second drive.

I changed the jumper on it to be a slave. I changed the IDE cable so that the 6 gig drive is plugged into the slave plug of the IDE cable where the 20 gig drive is, and plugged the other into my CD drive.

I boot up the machine, and it booted off of the 6 gig drive (old stuff was on the desktop).  I go into the partition manager, which shows the 20 gig drive with the boot flag on, and shows no such flag on the 6 gig.  I try to format, repartition, etc, etc on the 6 gig drive, and the system won't let me (probably because it is the drive the system just booted onto).

I then realize that my CD drive disappeared.  This is likely an easy fix.  I think I just need to change its jumper to 'master'.  I could have, however, ended up with some sort of convoluted cable arrangement.  If so, it's likely still an easy fix.

It is strange, though, that the system sees both hard drives just fine, it knows which one I prefer to be a boot drive (and also which one that I don't), the master and slave jumpers are right, and yet, it boots up on the wrong one.

Is there an easy answer to this?  I know I can disconnect the 20 gig drive, boot up on a windows startup floppy and format the 6 gig, and then work from there.  Or is it that the windows startup floppy *is* the easy answer.

Thanks in advance.  BTW - I am a happy ubuntu user, and I'm ready to graduate from my Dell 'let's try linux out' machine.  I may keep a windows box around for my family, but I see no reason to not load ubuntu into any machine I am personally using.  Ubuntu presents me with challenges, but I enjoy working through them (most of the time, anyway).  Some of the challenges are surely the age and speed of the machine I've installed ubuntu in to.

terry

---

### Post by wojox on 2009-08-16
Do you have the very end of the ribbon cable connected to the master drive?

---

### Post by Bucky Ball on 2009-08-16
You need to boot from the live CD. That would be easiest. That way ALL the drives and partitions will be UNmounted. They have to be unmounted to manipulate them. If it is booting from the 6Gb you are trying to wipe (which I think it is), then run the LIVE CD and use System->Admin->Partition manager. Format how you like then swap the drives back. Should be a breeze. You may have to set it up to mount at boot though, but that is easy and lots of HOWTOS.

---

### Post by ttoolin on 2009-08-16
Thanks for the help!  It never even occured to me to boot from the CD!!!!  I can think of a lot of times doing that might make things easier.

I will check my ribbon cables on all of my hardware.  I know I have to get my CD drive back in use, so I'll look at and fix all of the IDE wiring while I'm at it.

Thanks again!

---

