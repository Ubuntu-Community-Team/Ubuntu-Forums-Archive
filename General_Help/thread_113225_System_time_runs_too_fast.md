---
title: "System time runs too fast"
date: 2006-01-05
forum: General Help
---

### Post by rick333 on 2006-01-05
I'm running vmlinuz-2.6.12-10-amd64-k8-smp on an AMD64 dual-core CPU. Just installed a few days ago. I've noticed that the system time is advancing about 30 minutes too fast for every 12 hours. Anyone know what the problem is and how to fix it?

Thanks,

Rick

---

### Post by dcstar on 2006-01-06
[QUOTE=rick333]I'm running vmlinuz-2.6.12-10-amd64-k8-smp on an AMD64 dual-core CPU. Just installed a few days ago. I've noticed that the system time is advancing about 30 minutes too fast for every 12 hours. Anyone know what the problem is and how to fix it?

Thanks,

Rick[/QUOTE]
That could be your motherboard hardware clock out of whack, but if you install the ntp-server package you can have your system keep itself in sync with an external time server.

---

### Post by tokyovigilante on 2006-01-06
This is a kernel bug on AMD64 systems and certain motherboard chipsets. 

It's fully fixed in kernel 2.6.15, so if you can stand the instability, you could upgrade to the Dapper Drake development release.

2.6.12 also has the fix, so you don't necessarily have to upgrade if you don't want to run the less stable development version, but you need to also follow the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=53094"), which basically adds a boot option to your kernel.

---

### Post by rick333 on 2006-01-06
[QUOTE=tokyovigilante]This is a kernel bug on AMD64 systems and certain motherboard chipsets. 

It's fully fixed in kernel 2.6.15, so if you can stand the instability, you could upgrade to the Dapper Drake development release.

2.6.12 also has the fix, so you don't necessarily have to upgrade if you don't want to run the less stable development version, but you need to also follow the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=53094"), which basically adds a boot option to your kernel.[/QUOTE]

I checked System Monitor and don't seem to have the 50% CPU usage symptom  referenced in [URL="http://ubuntuforums.org/showthread.php?t=53094"]
http://ubuntuforums.org/showthread.php?t=53094[/URL]. Does this mean that I have another problem?

---

### Post by rick333 on 2006-01-06
[QUOTE=dcstar]That could be your motherboard hardware clock out of whack, but if you install the ntp-server package you can have your system keep itself in sync with an external time server.[/QUOTE]

I did this last night and setup to "periodically synchronize clock with Internet servers". This morning when I checked, my system time had skipped almost an hour ahead. However, the setting did not seem to be in the clockthere   applet, so I reset it. I'll post the result later today.

---

### Post by tokyovigilante on 2006-01-06
[QUOTE=rick333]I checked System Monitor and don't seem to have the 50% CPU usage symptom  referenced in [URL="http://ubuntuforums.org/showthread.php?t=53094"]
http://ubuntuforums.org/showthread.php?t=53094[/URL]. Does this mean that I have another problem?[/QUOTE]
It could very well do. Do you get the same problem with a non-SMP kernel - ie amd64-generic or amd64-k8? Does it happen in Windows?

I know there are compatibilities with earlier amd64 kernels and some early socket 939 motherboards, which may not all present the same way depending on your hardware. I haven't experienced them with my system, although it's only ever run the development version which has the 2.6.15 kernel.

I'd suggest giving the no_timer_check option a go first, then searching the forums for "amd64 clock speed", there are a number of other fixes people have tried. If something works for you great, otherwise as a last resort try the Dapper Drake development release. The Flight milestone releases are stable enough for daily use (IMHO) and if you only upgrade between flights (ie current one is Flight-2, hold off upgrading till Flight-3 is released) you shouldn't run into too many bugs.

I'd suggest just downloading the kernel.org 2.6.15 sources and compiling yourself, but the hardware detection system has changed from 2.6.12->2.6.15, and this would break your system.

Good luck anyway, sorry I haven't got any simple solutions for you.

---

### Post by rick333 on 2006-01-08
I ended up with an unplanned solution to this problem. Switched to 32-bit SMP to avoid all the other problems with 64-bit operation and the problem appears to have disappeared. Thanks to those who tried to help.

Rick

---

