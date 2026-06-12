---
title: "[SOLVED] grub error 16 on dual boot windows"
date: 2009-01-02
forum: General Help
---

### Post by plr4ever on 2009-01-02
Hello all and happy new years,

My system has a myriad of OS's, but my main two are Ubuntu 8.10 x64 and Windows XP Pro. The other day, grub started giving me error 16s about the partition not being readable or something. I have essentially come to the conclusion that i need to reinstall windows, but i dont seem to be able to mount the partition in ubuntu(or knoppix or puppy) and backup my files. in the LiveCDs i cannot even find the windows partitions. Also, the windows install cd doesnt recognize the 2 NTFS partitions as being valid windows partitions.

When i try to mount via the terminal i get 
```
 fuse: mount failed: Device or resource busy 
```
even though it is unmounted and unaccesible. 

Does anyone know how i can mount the drives and rescue my files?

---

### Post by plr4ever on 2009-01-04
Well i just mounted it with a Parted Magic CD, and then i rebooted into ubuntu and it mounted there, so i copied my files over and reformatted. Now running Windows 7

---

