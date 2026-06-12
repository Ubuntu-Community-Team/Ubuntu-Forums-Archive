---
title: "usplash(?) made my entire system read-only?"
date: 2009-05-12
forum: General Help
---

### Post by bittergourd on 2009-05-12
i was trying 2.6.30rc5 just now and it was all good.  then as i tried to fix "kinit: no resume image", i removed splashy and installed packages for usplash.  then i tried to restart again, a bunch of error came out for example
"return: 24: illegal number: blah blah"
and all sorts of "read-only file system" error whenever trying to write to disk.  and i can not edit configuation files, can't use aptitude or apt-get etc etc.  

btw, i edited my menu.lst file to removed splash option a long time ago and there was no problem until i stupidly installed usplash.  i imagine that i can boot from livecd and edit menu.lst, but will it solve the problem?

any suggestion for help?  thanks!

btw, i am pretty disappointed by the way jaunty handles intel driver and dri2/uxa and released unusable product for the very common intel video chips.  how is this problem addressed in other distro?  i wouldn't have run into this problem if i didn't have to try the new kernels...

---

### Post by bittergourd on 2009-05-12
bump

i can try to do 

mount -o remount,rw /

and then i was able to edit files.  after i removed usplash, nothing changed, and i still get a read-only system after reboot...

---

### Post by Tipped OuT on 2009-05-12
Just woke up *yawn*.

1. Try another kernel at boot.
2. Boot into Live CD and see if you can fix it with GParted.
3. Back up your stuff and re-install.

These are options, not a list. :)

---

