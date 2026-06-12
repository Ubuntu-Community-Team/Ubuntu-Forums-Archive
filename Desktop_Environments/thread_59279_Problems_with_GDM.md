---
title: "Problems with GDM"
date: 2005-08-23
forum: Desktop Environments
---

### Post by izmaelis on 2005-08-23
Inadvertently I deleted /etc/init.d/gdm so I can't do
```

sudo /etc/init.d/gdm stop|start|restart

```
How can I bring it back to life?  :neutral:

---

### Post by KingBahamut on 2005-08-23
apt-get remove gdm
apt-get install gdm

---

### Post by izmaelis on 2005-08-23
[QUOTE=KingBahamut]apt-get remove gdm
apt-get install gdm[/QUOTE]
Uhm... I have tried that already and it didn't work out.

---

### Post by KingBahamut on 2005-08-23
I guess Im trying to figure out how you inadvertently deleted gdm to start with.

---

### Post by izmaelis on 2005-08-23
I followed this [guide](http://ubuntuforums.org/showthread.php?t=57368&page=1&pp=10). And wanted to upgrade to latest NVIDIA driver. In that step where I had to delete /etc/init.d/nvidia-glx I mistyped "n" to "g" hitted Tab an Enter...  :-x

---

### Post by izmaelis on 2005-08-23
```

sudo aptitude purge gdm && sudo aptitude install gdm

```
solved my problem.

---

