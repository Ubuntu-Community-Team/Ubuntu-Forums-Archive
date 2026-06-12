---
title: "Ubuntu 10.04 Unexpected Inconsistency during every boot........."
date: 2012-03-07
forum: Desktop Environments
---

### Post by s4sarath on 2012-03-07
Hi ,

First of all i would like to remind you all of the same problems posted here, but almost all went up without a clean possible solution.

[http://ubuntuforums.org/showthread.php?t=1846194](http://ubuntuforums.org/showthread.php?t=1846194)

This is the previously mentioned thread.
So, guys is there any possible solution this headache. If so, please discuss here.
Thanks to all in advance.

---

### Post by typhoon_tip on 2012-03-07
Check the SMART data of your drive first, and post here, would be helpful. You can find them in Disk Management tool under System menu.

---

### Post by s4sarath on 2012-03-07
Hey disk management details means , the partition and volumes of my hard disk?

---

### Post by s4sarath on 2012-03-07
== START OF INFORMATION SECTION ===
Device Model:     ST3320418AS
Serial Number:    6VMV3XZ7
Firmware Version: CC46
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Mar  8 09:42:44 2012 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

### Post by typhoon_tip on 2012-03-07
Open Disk Utility, select your internal Hard Drive and then click "View Smart Data", there should be a status there "healthy" or "not-so-healthy" mentioned on top of a big list of items (depending on how old is the drive).

---

### Post by s4sarath on 2012-03-08
Yeah..i Just checked the status....

The disk is "healthy".

---

### Post by typhoon_tip on 2012-03-08
Sorry but the linked thread you provided talks about "total damages on a hard drive due to hardware failure", how are we supposed to help ? Are you sure you are having *exactly* the same situation ? Since your disk is "healthy", I think probably is not the same case... Can you describe better the "unexpected inconsistency"..? Some screenshot or explaining the symptoms in details may help as well.

---

### Post by s4sarath on 2012-03-08
yeah...exactly...

my problem is same as that mentioned in thread i have provided above......

---

### Post by typhoon_tip on 2012-03-08
Do you need to recover important data ?

---

### Post by s4sarath on 2012-03-09
there is not much data in there.
I am really concerned that, i have to run fsck check and command after every restart.
any possibilities dude?

---

### Post by typhoon_tip on 2012-03-11
This seems very weird, especially if the hard drive is healthy. Do you have another Hard Drive to test ? Moreover, have you set the HD Controller in SATA-**AHCI** mode in your BIOS settings ? I found that if the controller is left in "compatibility" mode, Ubuntu doesn't like this Windows-XP-compatibility-setting very much, and may behave weirdly (tested with 10.04 and 10.10).

---

