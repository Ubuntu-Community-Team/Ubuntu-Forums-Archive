---
title: "Re-format SDHC help please!"
date: 2009-01-11
forum: General Help
---

### Post by psyopper on 2009-01-11
Hello all. It's been a long time since the last time I posted anything. Hopefully someone can help out here. I recently got a Dell Mini9 (no, this isn't a Mini9 question...). I decided to do a fresh install of 8.10 this afternoon but accidentally installed it to the SDHC card I had in the machine instead of the HDD as one would expect to do.

After I got the install straightened out by reinstalling to the correct drive, now when I insert the SDHC card I get the following in dmesg:

```
[ 3620.429118] mmc0: new SDHC card at address 8fe4
[ 3620.430905] mmcblk0: mmc0:8fe4 SD08G 7761920KiB 
[ 3620.431132]  mmcblk0: unknown partition table

```

When I did the installation there was 2 partitions, one showing 0% and the other as 99%. I did the guided install onto this card and told it to use the entire drive. Have I just hosed my brand new SDHC card? I really can't afford to go our and get a new one, there has to be some way to recover this drive!

Help! Please??!?!

EDIT: I should add a few things here...

1. This card worked just dandy before I installed to it
2. When I rebooted after the accidental installation to this card it was still readable in the Dell/Ubuntu installation - that's how I figured out what was wrong
3. This problem is only after installing 8.10 i386 to the machine

---

### Post by psyopper on 2009-01-12
More information, I actually finally got an error message when coming out of suspend mode. Two of them actually:

```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

```
mount: wrong fs tyope, bad option, bad superblock on /dev/mmcblk0, missing codepage or helper program, or other error. In some cases useful information is found in syslog - try dmesg | tail or so
```

Seriously, the second message cuts off at so. I guess this a free bump. 

Any help out there?

---

### Post by psyopper on 2009-01-13
Wow - nothing? Really? There's no hope to unhose this card?

---

### Post by fragos on 2009-01-14
Sounds like you have 2 partitions on your card. Install and gparted to remove both partitions and reformat the card to FAT.

---

### Post by psyopper on 2009-01-14
> **fragos said:**
> Sounds like you have 2 partitions on your card. Install and gparted to remove both partitions and reformat the card to FAT.

gparted was the first thing I tried! Because the card wouldn't mount, gparted never saw it to let me futz with it. Thanks for the idea though! 

I actually resolved this the old school way- I returned the card to Best Buy as defective and got a replacement, which works wonderfully!

---

