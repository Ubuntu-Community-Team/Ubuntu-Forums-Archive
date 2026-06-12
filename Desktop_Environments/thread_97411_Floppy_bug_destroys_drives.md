---
title: "Floppy bug destroys drives"
date: 2005-11-30
forum: Desktop Environments
---

### Post by gwilson on 2005-11-30
I've been trying to get my floppy drive to work under Ubuntu. After reading and trying several fixes (such as [http://www.ubuntuforums.org/showthread.php?t=85777)](http://www.ubuntuforums.org/showthread.php?t=85777)), my floppy drive stopped working, even under Win ME. The disks I'm testing work fine in my other Windows ME system. Thinking I had a random failure, I went out and bought a Sony replacement drive. I installed the drive, and it worked fine under Windows by which I mean Win ME could read the drive and the system could boot from the floppy. I went back into Ubuntu Breezy 5.10 and continued troubleshooting the unmountable floppy drive problem, and now the new drive has failed just like the first one.  I cannot read floppies on this machine, even under Windows, and the floppies still work in the other Win ME system on the next desk.

So...  I wouldn't have thought it possible that Linux software could damage my hardware (floppy drives are no longer rocket science, I'd say) but that seems to be what is happening. I have tried things like completly powering down and resetting the CMOS setup, but the drive seems to be dead.

I'd appreciate your feedback and comments on this since it seems pretty weird. Other than this, Breezy has been working just great for me.

---

### Post by amohanty on 2005-12-01
what does:
sudo mount -t vfat /dev/fd0 /media/floppy

with a floppy in the drive return?

AM

---

### Post by gwilson on 2005-12-01
Thanks for the reply.

sudo mount -t vfat /dev/fd0 /media/floppy
Password:
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

The light goes on and the disk spins soundlessly before returning the error.

My fstab looks like this:

/dev/fd0        /media/floppy   auto    rw, user, noauto  0       0

GW

---

### Post by amohanty on 2005-12-01
Is the floppy readable on some other machine?

AM

---

### Post by gwilson on 2005-12-06
As I wrote:

I cannot read floppies on this machine, even under Windows, and the floppies still work in the other Win ME system on the next desk.

Don't go to any great trouble over this. I've decided to just do without the floppy drive. Still, it should be noted that the system did somehow drive two floppy drives out of range and ruin them both.

I suspect that it is some kind of conflict between fstab and Nautilus. When I remark out the fd0 line in fstab and try to mount the floppy using Nautilus, the system at leasts begins to mount the floppy as one would expect. Unfortunately, the drive is no longer mechanically functional.

I've been experimenting with a number of other distributions on my other system and am very pleased with Ubuntu and the community support. I would never switch at this point and just accept this as a temporary bug of the sort that might be expected from time to time.

Thanks for the input.

GW

---

### Post by cwaldbieser on 2005-12-06
[QUOTE=gwilson]As I wrote:

I cannot read floppies on this machine, even under Windows, and the floppies still work in the other Win ME system on the next desk.

Don't go to any great trouble over this. I've decided to just do without the floppy drive. Still, it should be noted that the system did somehow drive two floppy drives out of range and ruin them both.

I suspect that it is some kind of conflict between fstab and Nautilus. When I remark out the fd0 line in fstab and try to mount the floppy using Nautilus, the system at leasts begins to mount the floppy as one would expect. Unfortunately, the drive is no longer mechanically functional.

I've been experimenting with a number of other distributions on my other system and am very pleased with Ubuntu and the community support. I would never switch at this point and just accept this as a temporary bug of the sort that might be expected from time to time.

Thanks for the input.

GW[/QUOTE]

Do you think it could possibly be a short in the hardware?  I used to have an old C64 program that played the national anthem by moving the read/write head on my floppy drive around like crazy.  It made a lot of racket, but the drive was never damaged by it.  They always seemed like they could take a lot of abuse.

---

