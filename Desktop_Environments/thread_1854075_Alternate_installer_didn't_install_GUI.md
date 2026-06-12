---
title: "Alternate installer didn't install GUI?"
date: 2011-10-03
forum: Desktop Environments
---

### Post by rosser725 on 2011-10-03
So i installed ubuntu natty narwhal on my pc, and it dual boots with windows with the grub bootloader. When I boot into ubuntu i get a terminal screen and it asks for a login. when I login i can't figure out what to do. how do i get grub to work??

---

### Post by MG&amp;TL on 2011-10-03
Ah. The alternate installer does not HAVE a desktop. It's a CLI. If your web is connected, you could try:

```
sudo apt-get install ubuntu-desktop
```or your desktop of preference.

GRUB is working fine if you can boot into windows.

---

### Post by rosser725 on 2011-10-03
> **MG&TL said:**
> Ah. The alternate installer does not HAVE a desktop. It's a CLI. If your web is connected, you could try:

```
sudo apt-get install ubuntu-desktop
```or your desktop of preference.

GRUB is working fine if you can boot into windows.
I tried that but I get:




```
root@ubuntu: # sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package ubuntu-desktop
```:(

---

### Post by MG&amp;TL on 2011-10-03
Try:

```
sudo apt-get update && sudo apt-get upgrade
```

Then  the desktop command.

---

