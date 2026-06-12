---
title: "Support for hardware RAID (SATA)?"
date: 2006-09-10
forum: Desktop Environments
---

### Post by snakyjake on 2006-09-10
Does Ubuntu fully support hardware RAID (SATA)?

From what I've been reading, everyone seems to be going through hell trying to get Linux to work with SATA drives and RAID drives.  Has anyone succeeded?  How much trouble is it?  Is there a HOWTO or wiki?  

Thanks,

Jake

---

### Post by rasti121 on 2006-09-10
I have a SATA drive and no problems with it at all (drivers detected and loaded at first boot). Never tried RAID with SATA though, but remeber it was a big problem to have boot drive on it in some early versions (with IDE).

---

### Post by jjtechno on 2006-09-10
So has anyone been successful with SATA raid? Can it be done or should it be done instead of a dual boot? VMware on raid? Anybody tried it?
regards

---

### Post by radekrazor on 2006-09-10
Have look [here]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")
and [here]("https://wiki.ubuntu.com/FakeRaidHowto")
I got this working with Raid 0

---

### Post by snakyjake on 2006-09-10
radekrazor, great information.

Does anyone have instructions if I simply just want to read from my RAID1?

Scenario:

1.  Dual boot Windows and Linux from Drive 1.  This is where the OS, programs, etc are stored.

2.  Windows/Linux share Drive 2.  This is where data, music, etc is stored.

3.  Drive 1 is non-RAID.  Drive 2 is RAID1.

Thanks.

---

