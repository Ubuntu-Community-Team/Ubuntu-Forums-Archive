---
title: "Unable to mount external drive"
date: 2008-07-27
forum: Desktop Environments
---

### Post by jerrywo on 2008-07-27
I may have outsmarted myself.  I made a clone of my internal drive (see previous thread) and now I'm unable to mount it.

I tried "mount" from CLI
"Can't find disk in /etc/fstab or /etc/mtab

I ran GTParted.  It showed drive as /dev/fd0 read-write (read-only file system).  /dev/fd0 has been opened read-only.  Input/Output error during read on /dev/fd0.

I restarted the system and it appeared I was able to boot from my external drive (told the machine boot from USB-HDD).

Did I get to clever in making a cloned external drive?
Jerry

---

### Post by jerrywo on 2008-07-27
To add to my own post,

the permissions of the external drive are:
brw-rw----

the letter "b" meaning a blocked device file.  if that helps anyone
jerry

---

