---
title: "Need Help Mounting HD"
date: 2005-11-05
forum: Desktop Environments
---

### Post by kartoffeln on 2005-11-05
Hi all,

I am a newbie here to linux, I have installed Kubuntu and created a root account, I am not able to mount my windows partitions, i tried the command

mount -t vfat/hda1 /mnt/Windows/

I dont see any partitions...:( 

Please help

---

### Post by luna6 on 2005-11-05
try (you forgot /dev/)....
sudo mount -t vfat/dev/hda1 /mnt/Windows/

---

### Post by kartoffeln on 2005-11-05
[QUOTE=luna6]try (you forgot /dev/)....
sudo mount -t vfat/dev/hda1 /mnt/Windows/[/QUOTE]

i didnt use 'sudo'

thanx buddy   I'll try that right away :D

---

### Post by luna6 on 2005-11-05
was a typo, should be like this...
sudo mount -t vfat /dev/hda1 /mnt/Windows/

---

