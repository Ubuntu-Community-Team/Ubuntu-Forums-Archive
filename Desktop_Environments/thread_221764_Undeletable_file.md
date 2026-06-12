---
title: "Undeletable file"
date: 2006-07-24
forum: Desktop Environments
---

### Post by XAsmodeanX on 2006-07-24
I had my Xserver crash (just froze and looked distorted, couldn't kill it, couldn't switch to another terminal) and I had to do a hard reset (meaning the power switch).

Now when I boot into Ubuntu I get that blue screen saying that the X server can't start and the error is in that it cannot move the file /var/log/Xorg.0.log to /var/log/Xorg.0.log.old.  Upon closer inspection, it would seem that it's throwing this error because Xorg.0.log.old is undeletable, unmovable, un-anything.

I've tried the obvious, sudo rm Xorg.0.log.old and get a permission denied error.  I also tried a sudo su and then from root issue the rm command and I still get a permission denied.  I've tried sudo mv'ing it to any other file and I get permission denied also.  I changed the attributes to be world readable and writable and tried the above and I STILL get a permission denied error.

Some helpful/interesting info:
It is an ext3 partition.
xasmodeanx@matrix:/mnt/ubuntu/var/log$ sudo ls -la |grep Xorg           
-rw-r--r--    1 root       root        22555 2006-07-23 22:06 Xorg.0.log
?rwsrwsrwt  255 4294902015 16777215 16777215 1970-07-13 22:20 Xorg.0.log.old

xasmodeanx@matrix:/mnt/ubuntu/var/log$ sudo lsattr |grep Xorg.0.log.old 
lsattr: Operation not supported While reading flags on ./Xorg.0.log.old

xasmodeanx@matrix:/mnt/ubuntu/var/log$ sudo chown root Xorg.0.log.old 
chown: changing ownership of `Xorg.0.log.old': Operation not permitted

xasmodeanx@matrix:/mnt/ubuntu/var/log$ sudo shred Xorg.0.log.old 
shred: Xorg.0.log.old: Permission denied

This has to get resolved or else I can't start an Xserver.  That's unacceptable even though I love the CLI and browsing with lynx :D

---

### Post by JoWilly on 2006-07-24
This problem is often caused by filesystem errors.

Have you tried an fsck ?

---

### Post by theconley on 2006-07-24
If you like lynx, try w3m.  It's like meeting firefox, after thinking IE was cool.

~Conley

---

### Post by XAsmodeanX on 2006-07-24
No, I haven't run fsck against it.

edit: ran e2fsck -f /dev/hdb1
Got about a thousand errors.  Corrected them all.  Now will boot into Ubuntu and see if it's okay.

---

### Post by XAsmodeanX on 2006-07-24
Woot.  Worked like a charm.  Still, almost a thousand errors?  I thought ext3 was supposed to fix this problem?  Guess not.

---

