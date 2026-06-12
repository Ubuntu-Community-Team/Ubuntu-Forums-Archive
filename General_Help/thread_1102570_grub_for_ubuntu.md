---
title: "grub for ubuntu"
date: 2009-03-21
forum: General Help
---

### Post by jakespet on 2009-03-21
HI all,
I have two hard drives one of them, my "D" drive has Windows. I just installed  ubuntu 7.10 (currently in the process of upgrading to 8.04)and here's my problem: I cannot access my windows, I don't know if Ubuntu didn't detect it or couldn't find, but in any case it is still there. I checked under "my Computer Icon" and windows is still there.I didn't delete it. I tried to install grub, which comes back as 0 value.I pulled up my terminal and did an install but no luck. Does anyone have any ideas how get my grub to properly start? Thanks so much.
RH AKA jakespet

---

### Post by zvacet on 2009-03-21
You have to add Windows to your menu list.Type in terminal 

```
sudo fdisk -l
```

and post it here so somebody will help you do that.

---

