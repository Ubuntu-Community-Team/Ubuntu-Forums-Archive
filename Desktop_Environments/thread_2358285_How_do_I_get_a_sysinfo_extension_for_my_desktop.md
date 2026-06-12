---
title: "How do I get a sysinfo extension for my desktop"
date: 2017-04-11
forum: Desktop Environments
---

### Post by minecralex on 2017-04-11
Idk if I'm posting this in the right section or not, but I was wondering if anyone knew a plugin/mod type of widget which could be integrated into the desktop and show off all the sysinfo including CPU temp, used RAM, CPU freq., GPU temp, GPU usage, HDD/SSD usage, HDD/SSD speed/response time, etc. The reason that I'am asking is because online in various other forum threads, I see people showing off their desktops which look so awesome, with integrated live system information with etremely aesthetically pleasing bars and pie charts showing off the computer resources. A lot of the desktops that I see online are much better than any desktop that I have used so far. I would like to know if anyone knows any good programs/plugins I could use, and I'm sort of a desktop environment noob as I don't even know how to manage and install new desktop environments. (BTW: I'm currently using Gnome 3.18.5 according to inxi)

---

### Post by howefield on 2017-04-11
Somewhat depends on the desktop environment unless you want a conky setup.  

```
cat /etc/*-release
```
```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by gordintoronto on 2017-04-12
+1 for Conky and lm-sensors.

---

### Post by Frogs Hair on 2017-04-12
You have to be careful of version , not all Conky syntax will work properly on the version 1.10 which is the latest.
 [https://www.gnome-look.org/browse/cat/124/ord/latest/](https://www.gnome-look.org/browse/cat/124/ord/latest/)

---

