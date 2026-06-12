---
title: "[SOLVED] edit master boot record to use an existing grub install"
date: 2009-01-10
forum: General Help
---

### Post by beattyml1 on 2009-01-10
Awhile back I installed Ubuntu Studio alongside my existing install of ubuntu, but back then I did not know how to not install the boot loader so now my MBR boots the Ubuntu Studio install of Grub, now I want to try to make my master boot loader boot up the original Ubuntu grub install so that I am using the install that is associated with my primary OS (Ubuntu) how do I go about making my master boot record boot this grub install, my main goal in all of this is so that I can access all of my Grub settings from my primary OS

---

### Post by caljohnsmith on 2009-01-10
How about trying:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your Ubuntu Studio and original Ubuntu partitions in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2). Choose which one is the original Ubuntu install, given that:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
...etc.

```
So using the (hdX,Y) for your original Ubuntu install do:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how that goes or if you run into problems.

---

