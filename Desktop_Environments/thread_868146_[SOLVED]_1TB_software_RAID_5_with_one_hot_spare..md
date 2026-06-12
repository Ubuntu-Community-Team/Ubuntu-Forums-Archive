---
title: "[SOLVED] 1TB software RAID 5 with one hot spare."
date: 2008-07-23
forum: Desktop Environments
---

### Post by Impotence on 2008-07-23
I have been putting this off for a month, due to worrying too much about doing it wrong... i would appreciate it if someone would take me through this step by step.

_Distribution_ 
[LIST]
[*]Kubuntu 8.04 KDE4 remix (x86)
[/LIST]

_Hardware_
[LIST]
[*]3 x 500GB SATA drives (sdc,sdd and sde) [unformatted, unmounted] to be RAID 5'd.
[*]1 x 500GB SATA drive (sdb) [ext3, /home, 99% full] for a hot spare.
[/LIST]

The hot spare drive cannot be added until the array has been built as i do not have anywhere to store its contents (and the raid has been tested to death, I'm not wanting to loose 430GB of data!)

_What i have done so far_
[LIST]
[*]Tied up SATA data & power cables to stop them from moving
[*]Used hot glue to prevent sata data & power connectors from coming lose from HDD / Motherboard
[*]Installed mdadm
[/LIST]

_What i need to do (help!)_
[LIST]
[*]Create the RAID
[*]Setup RAID monitoring [audible alarm if a disk dies]
[*]create a lvm on it
[*]format the lvm (Suggestions? something journaled?)
[*]Create test data on the RAID (a copy of /home)
[*]Selectively drop individual disks out of the array (can't unplug them, dban them?) and learn to rebuild it.
[*]when i am confident that it is 'stable' mount it as /home
[*]Add the old /home disk (sdb) to the array as a hot spare
[*]Possibly use sdb to make a 1.5TB raid once i have filled 1TB (for future reference)
[/LIST]

_Questions_
[LIST]
[*]If i change distribution / when i do a clean install, how do i mount the raid? what files (if any) do i have to have a copy of to do it (such as the mdadm config file?)
[/LIST]

---

### Post by Impotence on 2008-07-30
I have managed to do it myself, my thanks to anyone who took the time to read my post but where unable to help.

I am currently writing up what i have learned in the form of a idiot proof distribution independent tutorial... I will post a link when it is complete.

I also plan to fill in [https://wiki.ubuntu.com/LVMOnRaid](https://wiki.ubuntu.com/LVMOnRaid) when i have finished!

---

### Post by flatline on 2008-08-28
Have you written up your guide yet?  I just found this post and am interested in your findings.  I currently have a RAID1 setup that I would like to add a hot spare to using mdadm, and I also need to setup monitoring - specifically, I need it to send me an email if the array has a disk failure.

Also - is your OS/bootloader on the RAID5 array?  I was just told that you cannot boot from a software RAID5 array.

Thanks!

---

