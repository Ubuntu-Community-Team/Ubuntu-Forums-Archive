---
title: "basero doesn't see blank media"
date: 2009-08-04
forum: Desktop Environments
---

### Post by cjsteele on 2009-08-04
I'm running Karmic (current as of today).  I am trying to burn an ISO with Basero as my normal user.  Said user appears to be setup properly...

cjs@sxf-cjsteele:~$ ls -l /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 2009-08-04 18:54 /dev/sr0
cjs@sxf-cjsteele:~$ cat /etc/group | grep cdrom
cdrom:x:24:cjs
cjs@sxf-cjsteele:~$ 

When I double-click on an ISO from Nautilus, it brings-up Basero pre-populated with my ISO image in the burn dialog, and asks me to put in a blank disc... problem is, I've got a blank disk in!

Furthermore, I can burn from command-line with wodim, a la `cjs@sxf-cjsteele:~$ wodim dev=/dev/dvdrw driveropts=burnfree -v -data /home/cjs/dlds/isos/myfavos.iso`

cjs@sxf-cjsteele:~$ ls -l /dev/dvdrw
lrwxrwxrwx 1 root root 3 2009-08-04 18:54 /dev/dvdrw -> sr0
cjs@sxf-cjsteele:~$ 


wth is wrong with basero?

---

### Post by drs305 on 2009-08-04
I had an identical problem with Brasero today on Karmic (64-bit). Rather than investigate, I installed gnomebaker and it worked properly.

---

### Post by cjsteele on 2009-08-05
thinking this needs to be a bug reported in Karmic

I'll do that after I get my new laptop up and going (downloading karmic iso now!  w00t)

-C

---

