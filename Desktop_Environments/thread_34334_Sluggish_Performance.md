---
title: "Sluggish Performance"
date: 2005-05-14
forum: Desktop Environments
---

### Post by _cashel on 2005-05-14
I'm new to the Linux scene, so I'm not all too sure of what I'm doing most of the time, so keep that in mind ;).

I've recently installed Hoary, and pretty much have everything to my liking except for one thing. The overall performance seems rather poor compared to that of Windows. I'm running an Athlon XP 2200+ w/ 512mb PC2700 ram and a 7200 RPM hard drive. The simple things seem to run slowly though. Switching tabs and scrolling in Firefox has a noticeable lag, and deleteing text will lag quite badly. Browsing the desktop just feels slugish as well. Finally, the actual loading of the OS is very slow. It just takes awhile trying to load everything before it reaches the login. I know partly why, it hangs trying to config the network devices, and I have haven't been able to get my wireless NIC to work just yet. However, that isn't all of what is slowing the startup down.

This may be sort of vague, but if you could help me fix this problem, I'd greatly appreciate it.

---

### Post by nad on 2005-05-14
Work is presently proceding to speed up the boot process. One way increase your speed is to recompile your kernel to include only the modules that you desire. You could also review the init scripts in /etc/rcS.d and /etc/rc2.d to find services that you do not need and delete them.

Unlike a M$ os install, the linux kernel loads required modules dynamically from its' libraries upon hardware probing.

As far as the desktop being sluggish, gnome is going through growing pains. You may wish to use the hdparm utility to increase your drive performance. There are other suggestions in these forums also.

Your system should certainly be able to perform satisfactorily given your hardware specs.

---

