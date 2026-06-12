---
title: "Setting mount options for removable media through Gnome"
date: 2008-08-09
forum: Desktop Environments
---

### Post by gronbaek on 2008-08-09
Hi, I just realised that it's possible to change some settings for removable medias through Gnome. Some of it works fine, but where can I see what mount options I can use? The removable disk uses NTFS and mounts in /media/disk with root:root as owner and 777 rights.
I would like to mount with my own username and group, but if I try change the options trough the settings dialogue, Gnome just reports an error. What options are available? Those from NTFS, or those from fuseblk, which Gnome reports the disk as the filesystem?
Right now the options are set as: user_id=0 and group_id=0, but i don't know how to change that into something useful.

Regards Gronbaek

---

### Post by plantatree on 2012-12-07
gnome3 uses  udisk as a backend [1]. For gnome 2 I see [2] but have not tested.


[1] [http://forums.gentoo.org/viewtopic-t-924802-start-0.html](http://forums.gentoo.org/viewtopic-t-924802-start-0.html)
[2] [http://people.debian.org.tw/~chihchun/2007/06/20/setup-mount-options-for-gnome-mount/](http://people.debian.org.tw/~chihchun/2007/06/20/setup-mount-options-for-gnome-mount/)

---

