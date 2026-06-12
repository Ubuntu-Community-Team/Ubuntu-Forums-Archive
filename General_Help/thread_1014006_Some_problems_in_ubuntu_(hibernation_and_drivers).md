---
title: "Some problems in ubuntu (hibernation and drivers)"
date: 2008-12-17
forum: General Help
---

### Post by LordOfDarkness on 2008-12-17
Hello. I have some problems with Kubuntu.

Hibernation and stand-by both give problems. The PC goes in hibernation/standby fine, but then when turning it on again it freezes at the kubuntu loading screen and I cannot do CTRL+F1 and the like either anymore. Though interesting to note, I can still log in remotely through SSH so it appears to be just X that won't resume properly from standby/hibernation.

I cannot use the official NVIDIA drivers, when I try to run KDM it just flickers and exits, runs fine again when i rollback to the previous xorg.conf. It's a Geforce 9600 GT with 512MB onboard memory.

---

### Post by justyjusty123 on 2009-02-14
I have  the same problem.  I also use an NVIDIA 9600GT graphic card.

I have 2 GB of memory and no swap space at all. Could this be the reason why my system "cannot wake up"? Any help/comment appreciated!

```

root@zockhobel:/home/cl# free
             total       used       free     shared    buffers     cached
Mem:       2021056     971280    1049776          0     141208     402584
-/+ buffers/cache:     427488    1593568
Swap:            0          0          0
root@zockhobel:/home/cl# swapon -s
Filename                                Type            Size    Used    Priority
root@zockhobel:/home/cl# 

```

---

