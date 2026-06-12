---
title: "How to remove icon from desktop?"
date: 2010-08-27
forum: Desktop Environments
---

### Post by VanillaMozilla on 2010-08-27
Mounting a disk automatically from /etc/fstab puts an icon on the desktop, whether it's appropriate or not.  How can I prevent this?  Is there an option?

I have two disks mounted with the commands

/dev/sda2 /media/Windisk ntfs-3g defaults 0 0

//machine/sharename /media/myshare cifs guest,uid=1000,iocharset=utf8,codepage=cp850  0  0

---

### Post by nick_goodfate on 2010-08-27
use ubuntu tweak. In Desktop icons section you can choose what you want to appear at your desktop.

---

### Post by ajgreeny on 2010-08-27
Or you can just give them a mount point somewhere other than /media, eg /mnt, as it is only volumes mounted at /media that appear on the desktop.

I can't comment on ubuntu-tweak as I have never seen it.

---

### Post by BrockStrongo on 2010-08-27
Both the suggestions above would work just fine.
 Ubuntu tweak is very easy to use and does have the option to show or not show mounted volumes

---

### Post by jimbop99 on 2010-08-27
The only problem with using Ubuntu tweak is it will prevent ALL devices mounted from appearing on the desktop. ie: flashdrives, portable drives.

---

### Post by VanillaMozilla on 2010-08-27
Wow, thanks for quick replies.  It works, but now there is a new (but smaller) problem.

Using /mnt makes it disappear from the hard drive, but it also disappears from the Places menu.  (I can still access it from the mount point, however.)

In other words,
/dev/sda2 /mnt/Windisk ntfs-3g defaults 0 0
works, but the disk disappears from the Places menu.  How do I get it back?

---

### Post by VanillaMozilla on 2010-08-27
OK, I got it.  Two methods:

1. From file browser, Bookmarks > Add Bookmark or Bookmarks > Edit Bookmarks...

2. edit ~./.gtk-bookmarks

---

