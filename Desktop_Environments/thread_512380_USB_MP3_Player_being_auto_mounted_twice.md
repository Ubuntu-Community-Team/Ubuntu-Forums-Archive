---
title: "USB MP3 Player being auto mounted twice"
date: 2007-07-29
forum: Desktop Environments
---

### Post by amac777 on 2007-07-29
First time is right after I plug in the usb device and an MP3 player icon appears on my desktop. The output of mount includes:

/dev/sda1 on /media/MP3 type vfat (ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

Then I right-click the MP3 player icon on my desktop and choose "Unmount Volume". The icon disappears only to immediately reappear. Here is the output of mount after this happens:

/dev/sda1 on /media/MP3 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

So it is mounted read only the first time, and then mounted rw the second time. Very bizarre.

When I then right click the icon and choose "Unmount Volume" for the second time, the volume is finally unmounted and stays that way. 

My desired operation is to auto mount the first time as rw and then only need to click "Unmount  Volume" once.

I've checked fstab -> no entries in there related to /dev/sda1....

Should I look somewhere else? Anyone got any suggestions?
Thanks for any help!

---

