---
title: "transform gnome's smb:// to mount for fstab"
date: 2009-05-05
forum: Desktop Environments
---

### Post by thinking on 2009-05-05
hi all

i have the problem that if i access a cifs share using my /etc/fstab mount command i cant change or read some files
if use smb://[LOCATION] in nautilus i can access it without problems

so the question i have is:
what mount-options are used by those gnome "mounts"? (i know they arent really mounted)
or where do i get info about those options?
or what would you search for?

thx all

---

### Post by element_G on 2009-05-05
it is a bit of a read but following [this](http://ubuntuforums.org/showthread.php?t=288534) worked for me

---

### Post by thinking on 2009-05-06
aaahhh
adding
gid=1000,uid=1000,nobrl
to my fstab options did the trick

thx for your help

---

