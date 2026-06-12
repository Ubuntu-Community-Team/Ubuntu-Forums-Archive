---
title: "Is there any way to activate advanced desktop effects in lxde ubuntu?"
date: 2008-07-27
forum: Desktop Environments
---

### Post by jittopjose on 2008-07-27
i installed lxde on ubuntu installation. let me know whether there any way to activate advanced desktop effects? i meant compiz effects? anybody have any idea about it?

---

### Post by Tim Sharitt on 2008-07-27
In a terminal 
```
sudo apt-get install compiz
```
to install compiz.

Run the command
```
compiz --replace
```
to start compiz from an already running session.

To set compiz as the default window manager, edit /etc/xdg/lxsession/LXDE/default and replace openbox with compiz.

---

### Post by jittopjose on 2008-07-27
its worked 
thanks friend..

---

### Post by jittopjose on 2008-07-27
but again there is a problem.  after reboot, it again openbox.. no compiz effects applied. i have replaced openbox with compiz in that default page. but no use. any idea about this?

---

### Post by jittopjose on 2008-07-27
i have added compiz --repace in autostart file in  /etc/xdg/lxsession/LXDE/autostart. now its works on startup also.
thanks

---

### Post by urukrama on 2008-07-27
It seems a bit odd to use a light desktop environment like LXDE to then use it with a heavy window manager. I don't use LXDE, but I suppose it might be easier to just create a custom CompizFusion xsession. See [this thread]("http://bbs.archlinux.org/viewtopic.php?id=51282") on the Arch forums for more info (most of it applies to Ubuntu, just replace pacman -S with sudo apt-get install).

---

### Post by jittopjose on 2008-07-27
i know compiz is somewhat heavy than openbox. in my old machine with P3 and 256 MB sd ram, i use lxde with openbox. but in my new one, it has amd 4400+ and 1GB ram, i replaced openbox with compiz. i like eyecandy effects and system resources also there.
lxde is light weight, but i feel that it is as usable as gnome. though it is less featured, its cool . i like its design and all. i dont like gnome's interface. kde also didnt satisfied me. but lxde is beautiful.
i wish in near future lxde will have more and more stable and feature rich.

---

