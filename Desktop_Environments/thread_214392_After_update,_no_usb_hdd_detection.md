---
title: "After update, no usb hdd detection"
date: 2006-07-12
forum: Desktop Environments
---

### Post by catfishy on 2006-07-12
Hiya, I'm pretty new to ubuntu, about six months.  After updates from update manager and an obligatory restart, I can't get the external usb drive to mount.  Disks (disks-admin) shows the drive there but crashes when I try to get any details on the drive.  It's frustrating because this is the second time I've ran into troubles with updates.  Does anyone else have this problem after July 12th's update?  Thanks so much for your help, buddies!

-----

I have since tried defraging using a windows machine (which read it fine) but it is still not mounting and still crashing disks-admin!  Thanks, any help would be very appreciated!

-----
The drive doesn't show up when I fdisk.
In disks-admin (it finally stopped crashing after several restarts) the external drive shows up but it can't give me any info about the drive except it says that it's in /dev/sda
When I try:  sudo mount -t vfat /dev/sda /media/BICYCLE
it tells me there's no device on /dev/sda
AHHHHH!  It makes me want to never update!
Frustrated, but still thankful for your help...

----------
Great.  By using an earlier kernel, 6 hours later I've been able to at least have ro rights on the drive, so i'll just keep fiddlin' with the fstab (there's plenty of help on that around here!)  thanks!

--------------
Turns out that the drive had to be checked and repaired (system mechanic on a windows machine did it while windows checkdisk couldn't).  So it had NOTHING to do with the UPDATE, just bad timing whatwith an update and the corruption of the disk.  Still scared of updates?  Yep.

The moral of the story is that even though my linux drive permissions were fine with me as the owner and with read/write access, it turned up as a "read-only disk" because there were disk problems that needed to be fixed first.  Pops up fine automagically with perfect permissions once fixed. YAY!

---

