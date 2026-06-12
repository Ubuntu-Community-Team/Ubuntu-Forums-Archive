---
title: "xscreensaver problem on fresh install"
date: 2005-05-25
forum: Desktop Environments
---

### Post by xmastree on 2005-05-25
So, I've upgraded to 5.04, and now xscreensaver doesn't work...

If I try to configure it from the desktop menu:
System > Preferences > Screensaver:

Cannot launch entry

Details: Failed to execute child process "xscreensaver-demo" (No such file or directory)


If I try to lock the screen:

Cannot execute 'xscreensaver-command -lock'

Details: Failed to execute child process "xscreensaver-command" (No such file or directory)


From a terminal:

chris@ubuntu:~$ xscreensaver
Segmentation fault
chris@ubuntu:~$

It appears to be installed:

root@ubuntu:/ # find -type f -name xscreensaver
./usr/bin/xscreensaver
root@ubuntu:/ # find -type d -name xscreensaver
./usr/share/doc/xscreensaver
./usr/share/xscreensaver
./usr/lib/xscreensaver
root@ubuntu:/ #

---

### Post by Burgundavia on 2005-05-25
Is this a warty upgrade?

Can you report a bug on this?

bugzilla.ubuntu.com

Corey

---

### Post by xmastree on 2005-05-25
> Is this a warty upgrade?No, it's a fresh install, I wiped my previous installation and started from a clean disk.


> Can you report a bug on this?Ok, done it now. It's [here](https://bugzilla.ubuntu.com/show_bug.cgi?id=11205)

---

### Post by xmastree on 2005-05-27
Turns out it wasn't a bug, it was my corrupt installation fle...

 :roll: 

Should have checked it first.

I'm now using the version which came with my 4.10 CD, and that works fine.
 :grin:

---

