---
title: "/dev/dvd SymLink issue"
date: 2006-09-25
forum: Desktop Environments
---

### Post by nukedathlonman on 2006-09-25
I haven't run into this on my other machines running Debian, and haven't been able to find a fix for this.  The symlink /dev/dvd is pointing to the wrong drive (my DVD burner at /dev/hdd).  I know the symlink should point to /dev/hdc.  I've tried several things to correct it, but it changes back to the wrong drive upon rebooting.  Anyone have any idea's on how to fix this?

---

### Post by kidders on 2006-09-25
Hi there,

The actual names of /dev entries are functionally irrelevant. If you still feel the need to play with them however, read a little about writing udev rules. You can use them to make any kinds of symlinks you want, as well as many other little tricks :-)

---

