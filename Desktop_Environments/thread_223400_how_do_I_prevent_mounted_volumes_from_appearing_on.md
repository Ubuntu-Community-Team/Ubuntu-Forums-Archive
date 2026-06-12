---
title: "how do I *prevent* mounted volumes from appearing on the desktop?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by djaya2 on 2006-07-26
Subject basically says it all.  I would like to stop gnome from placing icons for certain mounted volumes on the desktop.  (I don't want to see my two windows partitions on the desktop; nor do I want to see one of two partitions on my flash drive.)  Is this possible?  Thanks.

---

### Post by Buffalo Soldier on 2006-07-26
type **gconf-editor** at the terminal/command line and then proceed to navigating to apps -> nautilus -> desktop -> computer_icon_visible

---

### Post by djaya2 on 2006-07-26
Thanks---Unchecking volumes_visible gets rid of all of them.  Is there a way just to get rid of some?  I'd like to keep a couple.

---

### Post by endfx on 2006-07-26
If you don't actually want them mounted you could edit /etc/fstab
and comment out (put a # as the first character on the line) the drives/partitions that you don't want mounted.

Though, I have a feeling that you still want them mounted, you just don't want the icons to show up. I'm not sure how to do that.

---

### Post by emperor on 2006-07-26
When I want the partions mounted but just not visible on the desktop, I edit fstab and mount the partions to /mnt instead of /media. Everything mounted to /media will show up on the desktop.

---

### Post by endfx on 2006-07-26
good idea emperor.

---

### Post by djaya2 on 2006-07-26
Perfect, thanks.

---

