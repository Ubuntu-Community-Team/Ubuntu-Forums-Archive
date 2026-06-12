---
title: "Menu.lst UUID changing on software updates"
date: 2009-01-23
forum: General Help
---

### Post by AusIV4 on 2009-01-23
I've got a little problem with the menu.lst changing with software updates.

I have two computers that have distinct /boot partitions. When I did the installation, the /boot folder was part of the / partition, but for various reasons I've had to migrate /boot to another partition. Once I figured out how to do the transition, both systems worked fine for quite a while. 

Recently though, I've installed some system updates that replace menu.lst. Now, the update manager does ask whether to use the package maintainers version, or keep the old one. If I keep the old one, I have to manually edit menu.lst to get the new kernel version. If I install the new one, I have to manually edit menu.lst to point it back to the /boot partition.

What I want to know is where Ubuntu stores the UUID of the /boot partition for rebuilding the menu.lst. If I can change it at that source, then hopefully I won't have to manually edit the UUID in the future.

[EDIT]
I've come to the conclusion that the data was gathered from the lines that begin ```
# kopt
``` and ```
# groot
```Deleting menu.lst and running ```
sudo update-grub
``` has rebuilt a proper menu.lst.

---

