---
title: "Phantom CPU Utilization"
date: 2005-04-09
forum: Desktop Environments
---

### Post by jvoegele on 2005-04-09
I just downloaded and installed the new Hoary release yesterday, and I've been very impressed thus far.

However, I am having one problem, or annoyance rather, that I can't figure out.  According to gkrellm and gnome-system-monitor, my CPU usage is constantly hovering between 20% and 30%.  This isn't a big deal in and of itself, but the strange thing is that if I look at the process listing in gnome-system-monitor or top, the sum total of all the processes listed there add up to only about 5% utilization.  Whatever process is using the CPU to the 20% - 30% level is not there.  The only process that is consistently using *some* CPU is X, and it is only using 3% - 5%...nowhere near 30%.

Has anyone seen anything like this before?  Are gkrellm and gnome-system-monitor reporting the CPU usage incorrectly, or are there some "phantom" processes somewhere that I can't see with top or gnome-system-monitor?  (BTW, yes, I did tell gnome-system-monitor to list all processes, not just "my" processes.)

I'd appreciate any insight anyone can offer.

Thanks!

---

### Post by jdong on 2005-04-09
Try using **top** at a console to get the same statistics.


Note that there *are* some cases where you could get unexplained CPU usage, typically because Kernel-level drivers (i.e. webcam, NIC, etc) are using a huge amount of CPU. Heavily-threaded stuff also shows up deceptively.

---

### Post by c_dog on 2005-04-09
Also not having DMA set on for HD drives and CD drives will cause some heavy hits in sporatic CPU usage.

---

### Post by ubuntu_demon on 2005-04-09
there is also the option "all process" instead of viewing only your own processen in system monitor. But I prefer top.

---

### Post by jvoegele on 2005-04-10
[QUOTE=jdong]Note that there *are* some cases where you could get unexplained CPU usage, typically because Kernel-level drivers (i.e. webcam, NIC, etc) are using a huge amount of CPU. Heavily-threaded stuff also shows up deceptively.[/QUOTE]
Your advice helped me to track down the problem.  It was a package I installed called ifplugd that provides "hot plugging" for network interfaces.  I've uninstalled it, and things are back to normal.

Now I have to find a good replacement...

---

### Post by telmo on 2005-04-10
Lol

---

### Post by jdong on 2005-04-10
[QUOTE=jvoegele]Your advice helped me to track down the problem. It was a package I installed called ifplugd that provides "hot plugging" for network interfaces. I've uninstalled it, and things are back to normal.

Now I have to find a good replacement...[/QUOTE]

I strongly urge you to file a bug report ([http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)) against ifplugd. Otherwise, this problem may go undetected for releases to come! Please help Ubuntu be a better product, and maybe the devs will fix ifplugd for you!

---

### Post by jvoegele on 2005-04-10
[QUOTE=jdong]I strongly urge you to file a bug report ([http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)) against ifplugd. Otherwise, this problem may go undetected for releases to come! Please help Ubuntu be a better product, and maybe the devs will fix ifplugd for you![/QUOTE]
Should I still file the bug report even if ifplugd is not an officially supported package?

---

