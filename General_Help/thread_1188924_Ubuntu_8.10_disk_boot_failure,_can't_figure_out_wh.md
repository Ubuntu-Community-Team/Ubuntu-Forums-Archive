---
title: "Ubuntu 8.10 disk boot failure, can't figure out why."
date: 2009-06-16
forum: General Help
---

### Post by puffcorn on 2009-06-16
For some reason, Ubuntu won't boot now.  Everything was running fine, and then I started up the computer yesterday, and got the following:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

I've tried booting up several times since then, and this still happens.

I've had a similar problem a couple of times--the computer would freeze, and then I had to restart and got the same "DISK BOOK FAILURE, INSERT..." message.  However, those other times I was always able to boot up successfully after a while.

This time, it's been a couple of days, and it still won't boot.  I restored Grub, but that didn't help.

The hard drive itself seems fine, I can mount it and get to files when I use the live CD.

I would really like to be able to fix this.  I enjoy Ubuntu, but this is extremely frustrating.

Anyone have any insight as to why this is happening?  Like I said, everything had been running well and this came out of nowhere.  Maybe something got corrupted (that can hopefully be fixed)?

Any help would be greatly, greatly appreciated.

(I'm using 8.10, 756 MB RAM, 300 GB hard drive, 1.90 GHz processor... can provide other info if needed).

---

### Post by Waappu on 2009-06-16
Hi

It might be hardware problem. HD cable or motherboard hardrive controller.
I think you should check those.

---

### Post by puffcorn on 2009-06-17
> **Waappu said:**
> Hi

It might be hardware problem. HD cable or motherboard hardrive controller.
I think you should check those.

HD cable looks OK, but I'll double check anyway.

How would I check the motherboard hard drive controller?

Thank you for your reply.

---

### Post by Waappu on 2009-06-17
Hi

I do not have any good solution check HD controller.

But you can try boot another PC with your HD. If it boot ok, then probably problem is in your motherboard or HD cable.

Problem might also be in power supply.

---

### Post by puffcorn on 2009-06-18
When I use the live CD, I can mount the HD and access files.  I'm not totally sure--I'm far from a hardware expert, but that would seem to suggest that the HD cable is fine, and that the power supply would be OK as well. (But if I'm off-base here, please tell me).

I do plan on booting the HD in another PC, as you suggested.  That would certainly help to figure out what is happening here.  It'll probably be a couple of days before I get a chance to do that, though.

In the meantime, though, I am wondering if there could be another cause, besides hardware issues, that could cause these problems?  Maybe something like a corrupted file that could be fixed?

---

### Post by puffcorn on 2009-06-21
Well, I've been busy for the last couple of days, and haven't had a chance to use my computer until a couple of minutes ago... and this time, it booted up fine.

Anyone have any idea what is happening here?

As I said before, I'm no hardware expert, but my guess is the hard drive is about to die on me.  Is there anyone more knowledgeable than me who can back this up?

---

### Post by tashirosgt on 2009-06-21
Having recently had 3 hard drives die over a period of weeks, I think the odds favor your having a dying hard drive.  If it has the "smart" feature and that is enabled, you might look up on the internet how to read what it says about the drives condition.  I've never done that myself. 

Although it could happen, I have yet to encounter a hard drive problem caused by a cable,  IDE or SATA.   

When you boot from a cd, you can still use the dmesg command to look at what hardware is detected when you boot.  If you hard drive is dying, I would expect that you won't be able to detect the hard drive every time you boot from a cd.  (If you can detect it every time, then I don't know what's going on with your machine!)

---

### Post by puffcorn on 2009-06-21
I haven't used the dmesg command, but when using a live CD (both Ubuntu and Puppy), every time I've been able to mount the hard drive and access the files.  (So far, anyway).

Based on that, I guess I can't be completely certain that the HD is dying...

Thank you for your reply--I really appreciate it.

---

### Post by Johnny B on 2009-06-21
> **puffcorn said:**
> I haven't used the dmesg command, but when using a live CD (both Ubuntu and Puppy), every time I've been able to mount the hard drive and access the files.  (So far, anyway).

Based on that, I guess I can't be completely certain that the HD is dying...

Thank you for your reply--I really appreciate it.


double check your BIOS settings to make sure youre booting from that hard drive

---

### Post by puffcorn on 2009-06-22
Actually, I've checked the BIOS already.  The settings were OK, and I haven't made any changes to them.  Settings were the same whether I was able to boot or not.

Thank you, though, good suggestion.

---

