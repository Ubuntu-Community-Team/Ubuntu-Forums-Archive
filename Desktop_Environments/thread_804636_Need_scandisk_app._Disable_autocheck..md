---
title: "Need scandisk app. Disable autocheck."
date: 2008-05-23
forum: Desktop Environments
---

### Post by Mugsy323 on 2008-05-23
I have a dual-boot system with XP as my default OS booting from a raid-0 C: drive. Ubu-8.04 is on its own dedicated IDE drive.

As you know, Ubu occasionally does an automatic Disk Scan upon launch. Problem is, the damn thing tries to scan (and then "fix") my raid-0 C: drive, screwing up my system (over-writing my Master Boot Record!) **[COLOR="Red"]Argh![/COLOR]** I've complained about this before in other forums, but the Ubu developers have remained silent on this issue. :mad:

I need two things: **one**, how do I disable the autocheck so Ubu stops checking drives its not supposed to touch on startup?

And **two**: if I disable the autocheck, I'll need a replacement app that I can run manually to check the drive on demand. Any such creature exist?

I'll take what I can get in either order. Thanks.

---

### Post by sdennie on 2008-05-23
I assume you are talking about Windows software RAID.  It does really baffling things to the partition tables.

I don't recommend doing what I'm about to tell you to do because it's probably not a good idea but removing the symlink /etc/rcS.d/S30checkfs.sh will probably disable filesystem checking on bootup.

After that, you'd have to manually use fsck to check the various partitions.

---

### Post by VMC on 2008-05-23
> **vor said:**
> I assume you are talking about Windows software RAID.  It does really baffling things to the partition tables.

I don't recommend doing what I'm about to tell you to do because it's probably not a good idea but removing the symlink /etc/rcS.d/S30checkfs.sh will probably disable filesystem checking on bootup.

After that, you'd have to manually use fsck to check the various partitions.

How about instead of deleting that shell script, modifying it to just check the Linux partitions? 'man fsck' will give some help.

---

### Post by Mugsy323 on 2008-05-23
> **vor said:**
> I assume you are talking about Windows software RAID.  It does really baffling things to the partition tables.
I've never been 100% clear on the difference. I'm using the built-in Silicon Image Raid controller on my motherboard, but can't access it from things like the Windows Recovery Console (on the XP CD) until the necessary "drivers" are loaded. So I supposed it's "software" based.

But I'm not sure why it matters. I'm not trying to access it. I'm trying to prevent Ubu from doing so. :)

---

### Post by Mugsy323 on 2008-05-23
> **VMC said:**
> How about instead of deleting that shell script, modifying it to just check the Linux partitions? 'man fsck' will give some help.
Thanks, I'll look into that.

---

### Post by Mugsy323 on 2008-05-23
(deleted)

---

### Post by Mugsy323 on 2008-05-23
> **vor said:**
> I don't recommend doing what I'm about to tell you to do because it's probably not a good idea but removing the symlink /etc/rcS.d/S30checkfs.sh will probably disable filesystem checking on bootup.
I'm looking to edit the S30checkfs script, but there is no "obvious" line to edit (I want to limit it to checking just "/dev/sdb1"... my linux drive).

Any ideas? Thx.

---

