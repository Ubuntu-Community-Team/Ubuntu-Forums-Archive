---
title: "Ubuntu 6.06 and a RAID 5 Solution"
date: 2006-08-07
forum: Desktop Environments
---

### Post by InsaneShow on 2006-08-07
Hello Everybody.

Hopefully everyone is doing great.  I have a quick question.  I am slowly getting my feet wet with Linux.  My current linux box is:

AMD Athlon XP 2200+
1 GB DDR 400 Memory
1x 160GB IDE HD
... The rest of the specs are not that important

My motherboard supports a RAID 1/0 . . . however, I think I want to do a software RAID setup.  I am going to add two more 160 GB HD (however they will be SATA).  I will then put them into a RAID 5 configuration

From what I understand, this can be accomplished with the LVM, and because the LVM is a block level program it shouldn't matter that I will be using one IDE and two SATA drives.

My question is, lets say in a year, 320 GB of storage isn't enough for me.  Would it be possible to add another 160 GB drive to this disk array?  Does the LVM support adding a disk and reconfiguring without having to reinstall all my data.

It should be noted.  I do plan on installing all system files including the '/' directory to the RAID 5 setup.

Thanks
~InsaneShow

---

### Post by cantormath on 2006-08-07
> **InsaneShow said:**
> Hello Everybody.

Hopefully everyone is doing great.  I have a quick question.  I am slowly getting my feet wet with Linux.  My current linux box is:

AMD Athlon XP 2200+
1 GB DDR 400 Memory
1x 160GB IDE HD
... The rest of the specs are not that important

My motherboard supports a RAID 1/0 . . . however, I think I want to do a software RAID setup.  I am going to add two more 160 GB HD (however they will be SATA).  I will then put them into a RAID 5 configuration

From what I understand, this can be accomplished with the LVM, and because the LVM is a block level program it shouldn't matter that I will be using one IDE and two SATA drives.

My question is, lets say in a year, 320 GB of storage isn't enough for me.  Would it be possible to add another 160 GB drive to this disk array?  Does the LVM support adding a disk and reconfiguring without having to reinstall all my data.

It should be noted.  I do plan on installing all system files including the '/' directory to the RAID 5 setup.

Thanks
~InsaneShow

If your doing raid 5, arent you gonna need 5 160gb drives?

---

### Post by InsaneShow on 2006-08-07
No.  A RAID 5 can be accomplish on as few as 3 disks.

Your storage will be (N-1)*the smallest disk size, where N = number of disks.  RAID 5 uses two or more disks for storage and one disk that has the parity bits of those two or more disks.

Atleast that is my understanding

---

### Post by InsaneShow on 2006-08-07
Correction, I just described RAID 4.

RAID 5 is very similar in concept, but the parity information is spread out across all three or more disks along with the data.

---

### Post by RAOF on 2006-08-07
You can't (currently) do RAID 5 with LVM, sadly.  The appropriate dev-mapper kernel module just isn't there at the moment (except with the -mm series of development kernels).

LVM will currently do only RAID0 - striping, and it automatically does that.  On the other hand, it **does** allow you to transparently add (and even remove) discs from a running array, so that's cool :).

---

### Post by InsaneShow on 2006-08-07
Is it possible using a different tool then LVM, maybe EVMS or MDADM?

---

### Post by RAOF on 2006-08-07
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) says no.  At least for mdadm.  Mdadm uses the same *dm_foo* kernel modules as LVM.  I'm not sure about EVMS.

---

### Post by cleentrax on 2006-08-07
I've been trying to get a RAID-5 working with Ubuntu for a month now, with no luck. It's just not feasible right now, due to the fact that you can't boot to it. 

You can boot to a separate drive, but that doesn't make sense from a backup/uptime point of view, unless it's also part of a raid. And by this point we're talking 6+ drives in a single machine, which requires a massive tower and powersupply -- not exactly a low-power NAS kind of setup I was hoping for.

---

### Post by InsaneShow on 2006-08-07
Interesting . . . Does Ubuntu handle motherboard built in RAID controllers well?  My Windows XP MCE machine is an AMD 64 with a Asus MOBO that can support up to 6 SATA devices on a RAID 5.  It would be possible for me to switch the roles of these boxes.

---

### Post by hotani on 2006-08-07
Ubuntu will NOT do MB RAID. If you set it up on the MB, Ubuntu will boot right up and see 2, 3 or howevermany drives you have in there. It may be a different story with true hardware RAID using a card, I haven't worked with this config at all.

If you want RAID 5, I would recommend doing RAID-1 for your boot disk, then RAID 5 for your storage. You can pick up a couple of 80GB drives (or 40s even, but the price difference is small) for the RAID-1 and be done with it.

RAID 5 can be set up with mdadm (if you are into that sort of thing), or you could use the Alternate install disk which is what I did. My setup is 2x250GB RAID-1 and 120+300 LVM (RAID-0).

---

