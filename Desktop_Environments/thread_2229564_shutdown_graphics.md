---
title: "shutdown graphics"
date: 2014-06-13
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-06-13
Folks,

I need to copy a 250GB hard drive using dd, I would like to shut down all graphics and just work from the command line so that the system is running light.

I assume Ctrl-Alt-F1 would still have the desktop running on Ctrl-Alt-F7 so any tips appreciated.

Geffers

---

### Post by deadflowr on 2014-06-13
On Ubuntu switch to tty1 and run
```
sudo stop lightdm
```
for 14.04.(I think it works for 13.10 as well)
For 12.04 run
```
sudo service lightdm stop
```

---

### Post by Geoff_Lane on 2014-06-15
> **deadflowr said:**
> On Ubuntu switch to tty1 and run
```
sudo stop lightdm
```
for 14.04.(I think it works for 13.10 as well)
For 12.04 run
```
sudo service lightdm stop
```

Thanks, that was really useful.

Geffers

---

### Post by grahammechanical on 2014-06-15
You can also boot into recovery mode. That will give access to a Linux command line before the Gnome/Ubuntu desktop environment has loaded.

---

### Post by deadflowr on 2014-06-15
> **grahammechanical said:**
> You can also boot into recovery mode. That will give access to a Linux command line before the Gnome/Ubuntu desktop environment has loaded.

Just remember to remount it read/write.
(If you need to do anything.)
Easy way is to enable Networking first.
(This automatically resets it read/write)
or run
```
mount -o rw,remount /
```
from the root shell.

---

