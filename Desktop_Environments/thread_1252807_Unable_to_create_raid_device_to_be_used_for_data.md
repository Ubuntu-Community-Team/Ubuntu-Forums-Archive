---
title: "Unable to create raid device to be used for data"
date: 2009-08-29
forum: Desktop Environments
---

### Post by heathramos on 2009-08-29
I have installed Ubuntu to a hard drive that isn't on a raid without any issues.

At this point I am trying to set up a raid5 for 6 other hard drives but I have tried 3 times now to create the raid and each time the computer will eventually lock up (after quite a few hours).

How can I tell if one of the drives is bad?

more details:

I have 6 2tb WD drives which I enabled the TLER on.

I am able to see and create empty partitions on each drive using gparted and marked each to be used in a raid.

I issued the following command:

sudo mdadm --create --verbose /dev/md0 --level-raid5 --raid-devices=6 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1

after that, I looked at /proc/mdstat and was able to see the percentage complete. this takes forever but I saw it get as high as 60% before going to bed.

hours later, I check and the server is frozen and when I reboot and check, md0 wasn't created.

I looked at a coupl of log files and the only I can see that looked weird to me was a reference to the raid I was trying to create that said 5 of 6 drives were available and listed everyone except /dev/sdh.

which log files should I look at besides syslog and what should I be looking for?

my only other thought is to download software from western digital and start testing hard drives.

I guess it is always possible that it isn't a hard drive issue and my system just locks up after awhile and since this process takes so long it always locks up during it.

---

### Post by tgrimley on 2009-09-08
> **heathramos said:**
> I have installed Ubuntu to a hard drive that isn't on a raid without any issues.

At this point I am trying to set up a raid5 for 6 other hard drives but I have tried 3 times now to create the raid and each time the computer will eventually lock up (after quite a few hours).

How can I tell if one of the drives is bad?

more details:

I have 6 2tb WD drives which I enabled the TLER on.

I am able to see and create empty partitions on each drive using gparted and marked each to be used in a raid.

I issued the following command:

sudo mdadm --create --verbose /dev/md0 --level-raid5 --raid-devices=6 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1

after that, I looked at /proc/mdstat and was able to see the percentage complete. this takes forever but I saw it get as high as 60% before going to bed.

hours later, I check and the server is frozen and when I reboot and check, md0 wasn't created.

I looked at a coupl of log files and the only I can see that looked weird to me was a reference to the raid I was trying to create that said 5 of 6 drives were available and listed everyone except /dev/sdh.

which log files should I look at besides syslog and what should I be looking for?

my only other thought is to download software from western digital and start testing hard drives.

I guess it is always possible that it isn't a hard drive issue and my system just locks up after awhile and since this process takes so long it always locks up during it.

Your system shouldn't be locking up after a while.. that's not a good sign.  Usually thermal or memory issues.  Double check both.  You can look in dmesg | grep /dev/sdh to see if it reports anything.  Also, check the smart ("smartctl /dev/sdh" iirc) values to see if anything looks suspicious.  Mdadm should automatically continue rebuilding after a reboot (but I'm not sure about a hard lock, I would imagine it should as well there).

If a drive is dropping out this, is bad.  What does mdamd -D /dev/md0 say after you reboot?

---

