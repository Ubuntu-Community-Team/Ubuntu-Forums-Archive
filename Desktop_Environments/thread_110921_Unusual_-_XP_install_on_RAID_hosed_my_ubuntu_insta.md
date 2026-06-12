---
title: "Unusual - XP install on RAID hosed my ubuntu install on IDE0"
date: 2006-01-01
forum: Desktop Environments
---

### Post by eagle101 on 2006-01-01
Hi,
 
I have a Asus A7V333 with a Promise RAID controller + standard IDE 0

Ubuntu has been on IDE 0 for quite a while (Warty -> Breezy) 

Win2k has been on the Promise controller for a long time (installed before ubuntu).

Yesterday I formatted the RAID0 set and installed XP.  Now I can't boot into ubuntu.

I've never used a boot manager.  I just used BIOS to select the media I booted from (The menu where you boot from A:, IDE0, DVD, etc..)

Now I get "Target filesystem doesn't have /sbin/init"

So it looks like XP hosed GRUB that wasn't on the same disk or bus?  Why would it do that?  

Could someone give me a clue on what to do?  Thank You.

Happy New Year!

Dave

---

### Post by Sef on 2006-01-01
Most likely one of two things has happened:

1) If you had set up the first primary partition for XP, the install might have just wiped out GRUB, and by using a boot disk you could get into Ubuntu.

2) If you had not set up the first primary partition for XP, the install likely wiped out Ubuntu, and it will need to be reinstalled.  

When dual booting with Windows and Linux, Windows needs to be installed first.  If you have any questions on dual booting, just say you do, and I or someone else will help you.

---

