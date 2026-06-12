---
title: "Strange problem in Xubuntu 10.04 with usb devices..."
date: 2010-05-16
forum: Desktop Environments
---

### Post by night-wing on 2010-05-16
Hi there.
I just installed xubuntu 10.04. and noticed a strange problem, which was not in ubuntu 10.04. (gnome). It exists in thunar also as in pcmanfm:

When I plug in an usb drive (harddisc, usb-stick), I can see the content in the file browser. But I can't get deeper, than in the first directory (no deeper levels). When I start thunar or pcmanfm as sudo, I can!
The files or directories, I may copy as sudo to the internal hd are also not to be opened as a normal user.

Does anybody else have this problem and what may I do to make this work as normal?

Regards
nightwing

---

### Post by sedawk on 2010-05-17
What filesystem in on the usb devices?

If it is a extX filesystem, the owner of all directories
might be root and if the "x" flag for "others" is not
set only root is allowed to look inside the directories!

ls -l *
drwxr-xr-x 2 root root 4096 _timestamp_ allowed
drwxr-xr-- 2 root root 4096 _timestamp_ forbidden

---

### Post by XubuRoxMySox on 2010-05-17
It's easy enough to do it in PCManFM, though. Just click on **Tools > Open Current Folder as Root**. Then go as deep as you like within that folder. Thunar is cool, but I always keep PCManFM around for use with external media (backups and such).

Keeping it simple,
Robin

---

### Post by night-wing on 2010-05-17
The problem did not occur in ubuntu (gnome). The filesystem on the usb device is fat32 or ntfs - this does not make any difference.

---

### Post by 3Miro on 2010-05-17
I have a lot of problems with mount and unmount of UBS drives. What I ended up doing is install nautilus. When it comes to mounting, it handles things better than thunar (once something is mounted, you can easily use thunar).

---

### Post by night-wing on 2010-05-17
But in none of the previous ubuntu releases, I noticed this problem. Seems, that lucid is one more buggy ubuntu...

---

### Post by Jose Catre-Vandis on 2010-05-17
Try using Compact View, there is an unfixed bug with GTK. You are actually lucky the USB devices work, I had to fix that too by installing and running the hald daemon!

---

### Post by night-wing on 2010-05-20
Hi.
You were right. Compact View does it. But I still need detail view, because I always use it. Is there any way to fix the problem?

---

### Post by XubuRoxMySox on 2010-05-21
If **halevt** isn't installed, grab it (or try re-installing it). It's supposed to be the bridge between the Hardware Abstraction layer (HAL) and "Events" such as inserting a USB device or CD. Let us know if that fixes anything.

Still learning,
Robin

---

### Post by night-wing on 2010-05-21
Hi.
I'm sorry to say, but the installing of this package (and restart of course) did not change anything...
...only the directories with the german characters ü ö ä ... are not shown with any strange chars instead. But the only view to get into the deeper dirs is still the icon view or the list view - detail view doesn't work...

---

### Post by night-wing on 2010-05-24
bump

---

### Post by Jose Catre-Vandis on 2010-05-27
> **Jose Catre-Vandis said:**
> Try using Compact View, there is an unfixed bug with GTK. You are actually lucky the USB devices work, I had to fix that too by installing and running the hald daemon!

Todays updates to gtk have fixed the detailed view problem for me :)

---

### Post by night-wing on 2010-06-01
Seems to be solved. Thanks!

---

