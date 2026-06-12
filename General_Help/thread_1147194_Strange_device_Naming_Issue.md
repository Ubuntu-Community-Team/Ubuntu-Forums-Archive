---
title: "Strange device Naming Issue"
date: 2009-05-03
forum: General Help
---

### Post by satya_461 on 2009-05-03
Hi,

I installed ubuntu 9.04 on Dell M4300 laptop. I am a having device naming issue.

When I don't attach the external hard drive and booting to Ubuntu, my internal hard drive is recognized as as /dev/sda , so all the partitions are named /dev/sda1 ,/dev/sda2. Later inserting the external hard drive is named as /dev/sdb


When I attach the external hard drive and boot the device, the internal hard drive is named as /dev/sdb and the external hard drive is named as /dev/sda.


The external hard drive given by DELL is inserted by removing the cdrom and inserting the cdrom lookalike external harddrive.


Is there a way to fix the internal hard drive naming so that it always get /dev/sda??

The problem is I cannot add partitions into fstab file as naming sda, sdb keeps changing based on the external hard drive. :(

Please help..

---

### Post by spiderbatdad on 2009-05-03
not sure this is an external hdd if it gets inserted into a bay like that...at any rate, this sounds like something that would be configured in the system bios. Or does your removable drive have some jumper pins to select its role?

---

### Post by CatKiller on 2009-05-03
You might find something for setting the drive priority in the BIOS, but the sane solution for situations just like this is to use UUIDs to identify the drives in your fstab. The identifier at the start of the line would be UUID=<long string of text>, like ```
UUID=f0f60ece-7b14-40b8-aca3-c985d66ceac9       /               ext3    defaults,relatime       0       1
``` You can find the UUID for each of your partitions with ```
vol_id --uuid /dev/sda1
``` and so on.

---

### Post by spiderbatdad on 2009-05-03
> **CatKiller said:**
> You might find something for setting the drive priority in the BIOS, but the sane solution for situations just like this is to use UUIDs to identify the drives in your fstab. The identifier at the start of the line would be UUID=<long string of text>, like ```
UUID=f0f60ece-7b14-40b8-aca3-c985d66ceac9       /               ext3    defaults,relatime       0       1
``` You can find the UUID for each of your partitions with ```
vol_id --uuid /dev/sda1
``` and so on.

thank you for this useful post. I did get error:
```
localhost: ~$ vol_id --uuid /dev/sda1
/dev/sda1: error opening volume
Sun May 03

```
but sudo works fine.

---

### Post by satya_461 on 2009-05-05
It worked.. Thanks guys!!

---

