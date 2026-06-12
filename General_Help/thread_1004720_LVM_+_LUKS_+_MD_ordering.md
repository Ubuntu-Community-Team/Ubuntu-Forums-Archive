---
title: "LVM + LUKS + MD ordering"
date: 2008-12-07
forum: General Help
---

### Post by thehighhat on 2008-12-07
I have read several tutorials on using LVM2, and on encrypted filesystems with LUKS, and on raid implemented using MD.

However, there is some inconsistency regarding the order of LVM/LUKS.

The majority of docs say to use LVM2 on top of LUKS.  However, every time a new piece of hardware or partition is added to the volume group, one additional passphrase is required to unlock.  This is somewhat unweildy.  

In my tests, it seems that LUKS on top of LVM2 allows new hardware/partition to be added to a volume group, while keeping a single passphrase for the encrypted volume.

I am posting to find out if there are any security / data integrity / performance penalties associated with using LUKS over LVM2 (over MD RAID1).

Also to see what the community feels is best practice.

Please advise.


--------

graphically...


====MD1====|====MD2====|====MDn==== 
=========VG1===========|====VG2====
==LV1==|==LV2===|=LV3==|====LVn====
=ext3==|=LUKS===|=ext3=|====xfs====
=/boot=|=ext3===|=/var=|=/mnt/data=
_______|=/home==|______|___________

then I can add a new MD device to VG1, increase the size of LV2, and keep using the same single passphrase to encrypt all of /home.

But with LVM on top of LUKS on top of device (MDs), then I end up with multiple passphrase... which I want to avoid.

But above all, I want to protect data, avoid performance loss, and be secure.

---

### Post by thehighhat on 2008-12-08
any thoughts out there?

---

### Post by thehighhat on 2008-12-09
^^

---

### Post by andy75180 on 2009-04-25
You first setup the RAID then the LUKS then finally the LVM.

With this setup, you will only get asked for the passphrase once to unlock all the partitions on the LVM.

Here's my setup:

3x320GB Drives.

First setup the RAID arrays. Remember you can't encrypt the /boot so keep it seperate.

MD0 = RAID 1: /sda1 /sdb1 /sdc1 250MB
MD1 = RAID 5: /sda2 /sdb2 /sdc2 640GB

Set MD0 as /boot
Set MD1 as "physical volume for encryption"

Now all on MD1 will be encrypted.

You could put all your remaining partitions in this crypto area, but you'll get asked for the passphrase for each partition when booting up, which is annoying.
Better to set this crypto drive as "physical volume for LVM" and inside this LVM put all your other partitions. Only one passphrase then, just to unlock the LVM, which in turn unlocks all what is inside it.


It quite easy when you've done it a few times. Good luck.

---

