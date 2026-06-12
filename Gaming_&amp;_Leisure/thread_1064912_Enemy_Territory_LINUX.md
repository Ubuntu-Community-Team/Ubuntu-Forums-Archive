---
title: "Enemy Territory LINUX"
date: 2009-02-09
forum: Gaming &amp; Leisure
---

### Post by Colo2 on 2009-02-09
Hey, I downloaded ET and tried installing but got this error:

> tom@tom-desktop:~$ sudo sh et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/tom/.setup26632: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
tom@tom-desktop:~$ 

Please can someone help...
thanks :0

Tom

---

### Post by Perfect Storm on 2009-02-09
> error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

sudo apt-get install libgtk1.2

---

### Post by Vadi on 2009-02-09
You were missing libgtk1.2 as AI pointed out. [Click here]("apt:libgtk1.2") to install it.

---

### Post by Colo2 on 2009-02-09
Thanks :D I will try this soon.

---

### Post by betterhands on 2009-02-09
i just started playing this game today (on ubuntu about a month after only gaming on windows).  pretty fun.  had to do a little adjusting to get the sound to work for me, but things seem to be moving along...now just learning how to play the game :)

---

