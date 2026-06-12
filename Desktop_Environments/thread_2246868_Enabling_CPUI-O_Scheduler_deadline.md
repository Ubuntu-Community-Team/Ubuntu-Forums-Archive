---
title: "Enabling CPU/I-O Scheduler deadline"
date: 2014-10-03
forum: Desktop Environments
---

### Post by Shimbou on 2014-10-03
Salutations, I'm trying to figure out how you go about enabling deadline I-O scheduler on xubuntu. I've been trying to find something on it though google searches but, have had no luck finding anything that goes into detail or gives instructions on how to do it since I'm fairly new to linux I thought I might ask on the forums regarding it. I am trying to figure out how to do this so I can test to see if it helps my world of warcraft performance at all since its recommending as an option to increase fps in said game. So, does anyone know how to do this or know of a good articale detailing how to do so? Any help would be greatly appericated and thank you in advance.
~Shimbou

(Reference to suggested fix I referenced in my question in the link below).
[https://wiki.archlinux.org/index.php/World_of_Warcraft#CPU.2FI-O_Schedulers.3D](https://wiki.archlinux.org/index.php/World_of_Warcraft#CPU.2FI-O_Schedulers.3D)

---

### Post by Doug S on 2014-10-03
Hi and welcome to Ubuntu forums.

I guess I do no understand your question, because the link you gave tells you how to do it.

I suspect you will find that the "deadline" I/O scheduler is already the default. Example: ```
doug@s15:~/temp-k-git-3.10rc4/linux$ [COLOR=#ff0000]cat /sys/block/sda/queue/scheduler[/COLOR]
noop [COLOR=#ff0000][deadline][/COLOR] cfq
```I can also observe in the kernel config file:```
doug@s15:~/temp-k-git-3.10rc4/linux$ [COLOR=#ff0000]grep IOSCHED /boot/config-3.13.0-36-generic[/COLOR]
CONFIG_IOSCHED_NOOP=y
[COLOR=#ff0000]CONFIG_IOSCHED_DEADLINE=y[/COLOR]
CONFIG_IOSCHED_CFQ=y
CONFIG_CFQ_GROUP_IOSCHED=y
[COLOR=#ff0000]CONFIG_DEFAULT_IOSCHED="deadline"[/COLOR]
```

---

### Post by Shimbou on 2014-10-04
Salutations Doug, it would seem you are correct and thank you for the commands that was what I was looking for so I could have a look in the terminal. \\:D/ On another note got most of my programs working under linux just trying to improve performance for that perticuler game so, I suppose I'll keep looking might look into buying a motherbaord with the L3-allocation Option might be what I'll have to do which is fine.

---

