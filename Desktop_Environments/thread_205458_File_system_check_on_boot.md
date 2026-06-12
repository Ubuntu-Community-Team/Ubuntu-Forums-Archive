---
title: "File system check on boot"
date: 2006-06-28
forum: Desktop Environments
---

### Post by ahaslam on 2006-06-28
Hi,

Am I right in saying that if you have any ext3 partitions, a filesystem check will be done on every 30th mount?

This certainly seemed to be the case, but I've booted about 50-60 times since the last check. Has one of the numerous recent updates stoped this function, or have I developed a fault?

Cheers,

Tony.

---

### Post by woedend on 2006-06-28
try this(REPLACE hda1 with your partition if its different)
sudo tune2fs -l /dev/hda1

look for Maximum mount count.   If this value is 0, its disabled.  If its anything but 0 and you are not getting checking, there is another problem.  If it IS 0 and you want to enable it, you would do it like so
sudo tune2fs -c 30 /dev/hda1
to turn on checking every 30th mount
or use -i  if you'd rather set it by time instead of mounts.

---

### Post by ahaslam on 2006-06-28
[QUOTE=woedend]try this(REPLACE hda1 with your partition if its different)
sudo tune2fs -l /dev/hda1[/QUOTE]
Thank you, all is good. Running 'tune2fs' showed a mount count of 28, after *3* reboots the check commenced.

One of the 70+ updates must have reset the counter. I feel a little silly though, if I'd waited another day I wouldn't have needed to ask about it. :roll: 

Thanks again,

Tony.

---

