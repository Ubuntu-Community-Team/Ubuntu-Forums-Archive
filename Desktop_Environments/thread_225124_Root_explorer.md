---
title: "Root explorer"
date: 2006-07-29
forum: Desktop Environments
---

### Post by music_man on 2006-07-29
Hi

How can I open a explorer window as root please? I managed it before but I can't find how I did it.

Cheers

---

### Post by codejunkie on 2006-07-29
> **music_man said:**
> Hi

How can I open a explorer window as root please? I managed it before but I can't find how I did it.

Cheers
press alt+F2 and enter```
gksu nautilus
```also follow this link it will explain how to create a root launcher in your gnome menu hope this helps.
[http://ubuntuguide.org/wiki/Dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus](http://ubuntuguide.org/wiki/Dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus)

---

### Post by kane_666 on 2006-07-29
in ternminal type: sudo nautilus (there may be a prefix need, i cant member..)

---

### Post by ardchoille on 2006-07-29
> **kane_666 said:**
> in ternminal type: sudo nautilus (there may be a prefix need, i cant member..)

It's not a good idea to use sudo with graphical apps, sudo is for command line. If you want to run graphical apps as root, use gksudo or gksu.

---

### Post by ESPOiG on 2006-07-29
thats how i do it, because it is bad to use sudo with gui apps :D... gksudo nautilus

---

### Post by goatmale on 2006-07-29
Why is it bad to use sudo with graphical apps?

---

### Post by ardchoille on 2006-07-29
> **goatmale said:**
> Why is it bad to use sudo with graphical apps?

It can change the graphical app configs or the .ICEauthority file in your home directory. I've seen "sudo nautilus" save root's nautilus config to the user's home directory (over-writing the user's nautilus config) and mess up nautilus settings.

---

### Post by aysiu on 2006-07-29
> **goatmale said:**
> Why is it bad to use sudo with graphical apps?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ardchoille on 2006-07-29
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Very good explanation. Thanks for posting it :)

---

