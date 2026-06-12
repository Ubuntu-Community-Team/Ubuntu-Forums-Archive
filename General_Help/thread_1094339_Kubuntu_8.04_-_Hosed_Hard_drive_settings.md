---
title: "Kubuntu 8.04 - Hosed Hard drive settings"
date: 2009-03-12
forum: General Help
---

### Post by TWarn on 2009-03-12
Hi:

I inadvertantly removed the partition 2 (1K) in
   System Settings -> Advanced -> Disk & Filesystem

Of cource, now the system won't boot.  Is there a way to put it back?

Thanks Ted

---

### Post by kestrel1 on 2009-03-12
Depends on what was on it.

---

### Post by TWarn on 2009-03-12
Whats it used for?  I put the hard drive in another system and was able to read the files on the drive.

---

### Post by SuperSonic4 on 2009-03-12
> **TWarn said:**
> Hi:

I inadvertantly removed the partition 2 (1K) in
   System Settings -> Advanced -> Disk & Filesystem

Of cource, now the system won't boot.  Is there a way to put it back?

Thanks Ted

If it's only 1K it's likely to be part of the MBR or stage 2 of booting. I'd look into reconfiguring grub

---

### Post by TWarn on 2009-03-12
Hi I am a bit of a newbie to Linux. Is there any Doc's on what to do in Grub?  What to set, etc.

Thanks
Ted

---

