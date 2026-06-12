---
title: "Gnome+kde?"
date: 2008-05-08
forum: Desktop Environments
---

### Post by tvetter05 on 2008-05-08
Is it possible to have both Gnome and KDE on the same install of Ubuntu?

---

### Post by amingv on 2008-05-08
Yes, just install the one you don't have:

```
sudo apt-get install ubuntu-desktop #gnome
```
```
sudo apt-get install kubuntu-desktop #kde
```

---

### Post by zach382 on 2008-05-08
Yep just do what amingv said. When you reboot look in the sessions menu on your login window *before you login* and youll see an option for kde or gnome.

---

### Post by amingv on 2008-05-08
> **zach382 said:**
> Yep just do what amingv said. When you **reboot** look in the sessions menu on your login window *before you login* and youll see an option for kde or gnome.

We do not teach bad customs here, OK? :)(j/k)
Just press Ctrl + Alt + Backspace.

---

### Post by tvetter05 on 2008-05-08
sweet thanks, its downloading right now...

---

### Post by villindesign on 2008-05-09
does ```
sudo apt-get remove kubuntu-desktop
``` remove all the files installed by ```
sudo apt-get install kubuntu-desktop
```?

---

### Post by tattrat on 2008-05-09
This will remove all the executable files, but leave any configuaration files. Use "purge" instead of "install" to remove everything. Or if you use sunaptic package manager, select, "mark for complete removal" rather than "mark for removal"

---

### Post by villindesign on 2008-05-09
After using the command ```
sudo apt-get install xubuntu-desktop
``` I tried to remove the packages installed with that command by :```
~$ sudo apt-get autoremove xubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]?
```But, the command only uninstalls 1 package... Is there a way to remove all packages installed by the first command?

---

### Post by Xiong Chiamiov on 2008-05-09
I think that doing a 
```

sudo apt-get remove xubuntu-core

```
will do the trick.  I also think that there's some difference between apt-get and aptitude when it comes to matters like this, but I don't completely understand what it is.

---

