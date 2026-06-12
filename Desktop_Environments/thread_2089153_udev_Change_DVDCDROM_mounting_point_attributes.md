---
title: "udev: Change DVD/CDROM mounting point attributes"
date: 2012-11-28
forum: Desktop Environments
---

### Post by KroMignon on 2012-11-28
Hi all,
I would like to change the default attributes for the DVD/CDROM mounting point to add the execution flag.

I have some DVD/CDROM with shell scripts and when I insert them in my DVD drive, the DVD is mounted as read only, so I can run scripts from the DVD support.

Is it possible to change/complete the udev rules to change default attribute to 555 ?
udev is very strange/complicate for me to understand and I need help from expert.

Today, to do this I first unmount the default mount point create by udev when I insert the DVD:
```
% sudo umount /media/volume_name

```And create a new mounting point, and mount myself the DVD like this:
```
% sudo mkdir /mnt/dvdrom
% sudo mount –o ro,nosuid,nodev,noauto,uid=1000,gid=1000,mode=0555 /dev/sr0 /mnt/dvdrom

```Is there a way to do it in a "smarter way" ?

Regards

Fabrice

---

### Post by dannyboy79 on 2012-11-28
can't you add a line to your fstab with your specific mount options? I am not sure how to turn off the automount feature of udev however. Maybe this is of some help?
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by KroMignon on 2012-11-29
Thanks for the link dannyboy79.

I will check this and try to understand.... it looks very complicate to me!

---

