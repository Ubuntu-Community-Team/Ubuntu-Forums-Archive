---
title: "CPU scaling doesn't work anymore"
date: 2006-09-09
forum: Desktop Environments
---

### Post by gumbeto on 2006-09-09
Hi. I have ubuntu dapper on a toshiba labtop with a pentium M 2.0GHz processor. Since I installed ubuntu, the CPU frequency scaling always worked perfectly until about a week ago.
It was some day when I installed and uninstalled wine and xMule. I also installed some things through easyubuntu.
Next time I noticed (I think it was after rebooting the pc) the CPU frequency scaling monitor was always indicating the maximum frequency. I did dpkg-reconfigure to the gnome-applets package so I could manually change the frequency and the governor, after I read on some post that it was possible. I was able to change it manually but none of the governors work, except for performance and powersave, because the others keep the frequency always on it's maximum.
The first thing I do now when I log into ubuntu is to decrease the frequency, otherwise the laptop will completely turn my room into an oven.
I tried to uninstall powernowd and to do it through the kernel modules as I read on [http://ubuntuforums.org/showthread.php?t=248867&highlight=userspace]("http://ubuntuforums.org/showthread.php?t=248867&highlight=userspace")
It didn't have any effect and I installed powernowd again instead.

I can't figure out how to solve this. Did anyone had the same problem and was able to fix it?

Thanks a lot folks
Gumbeto

---

