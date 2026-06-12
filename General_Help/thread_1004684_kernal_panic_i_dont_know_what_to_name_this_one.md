---
title: "kernal panic? i dont know what to name this one"
date: 2008-12-07
forum: General Help
---

### Post by stonedparadox on 2008-12-07
right..
it started OF as why my 2 externals have changed to read only and i wanted to find out why this was happening so i googled
and i got this


[https://answers.launchpad.net/ubuntu/+question/3620](https://answers.launchpad.net/ubuntu/+question/3620)
it didnt really help me 
but i was curious as to what dmesg did 
but i get this ..
[99604.561490] FAT: Filesystem panic (dev sdc1)
[99604.561498]     fat_get_cluster: invalid cluster chain (i_pos 0)
[99605.559774] FAT: Filesystem panic (dev sdc1)
[99605.559782]     fat_get_cluster: invalid cluster chain (i_pos 0)
[99606.558061] FAT: Filesystem panic (dev sdc1)
[99606.558069]     fat_get_cluster: invalid cluster chain (i_pos 0)
[99607.556709] FAT: Filesystem panic (dev sdc1)
[99607.556718]     fat_get_cluster: invalid cluster chain (i_pos 0)
[99608.554644] FAT: Filesystem panic (dev sdc1)
[99608.554652]     fat_get_cluster: invalid cluster chain (i_pos 0)

thats only a bit of it.. 
i didnt wanna spam this topic with all of it ..but it goes on for a bit

what does that mean?
is it like the old defrag thing on windows when clusters were all over the place?


im still kinda curious to the file system yokie but ill keep looking
is the other thing serious?

---

### Post by cariboo on 2008-12-07
I would suggest you run chkdsk on the drive in question, as it looks like there is some kind of problem. You have to boot into Windows to run chkdsk on the drive.

If you don't have Windows, you run testdisk on the drive, and repair the problem. Testdisk is in the repositories, and you can get more info here:

[http://www.cgsecurity.org/wiki/Advanced_FAT_Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

Jim

---

