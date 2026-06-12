---
title: "ROOT login crashed KDE"
date: 2006-12-07
forum: Desktop Environments
---

### Post by kapilg_it on 2006-12-07
:confused:  every thing was fine in gnome ,untill recently i installed kubuntu-desktop
i logged in as root and system slows down saying " the process for the system protocol died unexpectedly"

konquerer failed , and all the x-windows are displayed without title bar (you cant move them)
I logged in as un-previleged user and KDE worked at its best even better than GNOME.
no idea about y the KDE misbehaved with root :-D

---

### Post by ComplexNumber on 2006-12-07
> **kapilg_it said:**
> :confused:  every thing was fine in gnome ,untill recently i installed kubuntu-desktop
i logged in as root and system slows down saying " the process for the system protocol died unexpectedly"

konquerer failed , and all the x-windows are displayed without title bar (you cant move them)
I logged in as un-previleged user and KDE worked at its best even better than GNOME.
no idea about y the KDE misbehaved with root :-D
what on earth are you doing logging in as root? i guess you must have enabled the root account. the reason why they were displayed without the titlebar is because kwin has crashed.

btw wait until you have customised kde to the full, and you will notice that kubuntu will slow down.

---

### Post by kapilg_it on 2006-12-07
root login worked in gnome well......though some  sytem->administration task are not there .
KDE was working fine with improved looks but i still have a keen desire know the solution to failure of system protocol process.....8)

---

### Post by kapilg_it on 2006-12-07
> **ComplexNumber said:**
> what on earth are you doing logging in as root? i guess you must have enabled the root account. the reason why they were displayed without the titlebar is because kwin has crashed.

btw wait until you have customised kde to the full, and you will notice that kubuntu will slow down.

does root logins on a destop system pose some threat :-k

---

### Post by ComplexNumber on 2006-12-07
> **kapilg_it said:**
> does root logins on a destop system pose some threat :-k
of course it does. when root, you can do anything (including destroying your system). also, **NEVER EVER EVER** login as root whilst connected to the internet.

---

### Post by kapilg_it on 2006-12-07
> **ComplexNumber said:**
> of course it does. when root, you can do anything (including destroying your system). also, **NEVER EVER EVER** login as root whilst connected to the internet.

but when you login as non-root working in nautilus or konquerer  dont let you manage file system easily ( like viewing files set by root in non-read perm. ) for that i have to use terminal , thats fine but :-|  but i donot login as root normally..

is there any way to make sure that KDE runs fine in root mode also ....i have updated to xfce -desktop meanwhile this post

---

### Post by maniacmusician on 2006-12-07
it's just not smart to run as root. There's no reason to do so. IF you need root priveleges, just use sudo. if you need them for a period of a few minutes, just do "sudo su" and then close the terminal when you're done. but logging in as root exposes your entire system. If you get  hijakced or hit by a virus, then the hijacker/virus will ALSO have root priveleges and will be able to do anything it wants to your system. when logged in normally, it can only touch your /home/user folder.

---

### Post by darkhatter on 2006-12-07
ubuntu has done alot of weird things to their system, which messes up alot of things in root. I have no idea how to fix it. but if you 

hit alt+f2 and type "kwin --replace" you should be able to move windows.

---

### Post by kapilg_it on 2006-12-07
> **darkhatter said:**
> ubuntu has done alot of weird things to their system, which messes up alot of things in root. I have no idea how to fix it. but if you 

hit alt+f2 and type "kwin --replace" you should be able to move windows.

presently moved to xfce : will give this a try for sure ](*,)

worked under mepis for a very long time but KDE never gave such error like " system protocol..."

---

### Post by aysiu on 2006-12-07
> **kapilg_it said:**
> but when you login as non-root working in nautilus or konquerer  dont let you manage file system easily ( like viewing files set by root in non-read perm. ) for that i have to use terminal , thats fine but :-|  but i donot login as root normally..

is there any way to make sure that KDE runs fine in root mode also ....i have updated to xfce -desktop meanwhile this post
That's when you create a launcher for ```
kdesu konqueror
``` or ```
gksudo nautilus
``` Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, I've moved your thread to a more appropriate place.

---

### Post by kapilg_it on 2006-12-07
- i was just looking for that..This sure will help me for the KDE problem
 Excellent help thank you aysiu

---

