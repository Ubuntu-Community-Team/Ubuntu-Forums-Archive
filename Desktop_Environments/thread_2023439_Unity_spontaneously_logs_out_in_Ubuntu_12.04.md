---
title: "Unity spontaneously logs out in Ubuntu 12.04"
date: 2012-07-12
forum: Desktop Environments
---

### Post by yang on 2012-07-12
This started happening after I upgraded from 11.10. I'm running on a Latitude 13 laptop with an Intel Mobile 4 Series Chipset Integrated Graphics Controller (not Nvidia) - no proprietary drivers. It seems to happen under load, though I can't tell if the load is caused by something with this problem or by a program I'm running.

I'd like to try nailing this problem. Ideally I don't want to switch to something else (at least not before knowing that that's the only way out and that it's specific to Unity and not, say, X).

---

### Post by IOSilver on 2012-08-19
Got the same problem, Big head ache for us.

NVidia drivers / NVidia Geforce 9800 GT

---

### Post by The_Autonomist on 2012-08-20
same problem here, except i'm on gnome.

---

### Post by 5l4y3r on 2012-08-23
Try to use Ubuntu 2D or proprietary drivers from nVidia.

---

### Post by asw24 on 2012-08-24
same problem here. Just upgraded from 10.04 to 12.04. already twice in the past hour. Requires me to reopen open applications. This really is a problem. 
i7 processor, gigabyte board with 6 GB Ram and nvidea videocard.

Ps: in the hardware list no 2D option. And within the new menustructure I am still lost to dive deeper. My normal tools are hidden. So far not good.

Pps: left the sytem unattendend for about 1 hour. Screen completely disappeared and showed snow on the upper 20% in blocks...This is not good. I have tried to adress autosleepfunctions etc. What I can find is set to 0 but still without affect.

---

### Post by Karlchen on 2012-08-24
Hello, yang.

[SIZE=1] (No idea whether you are still monitoring your own thread after 6 weeks and whether you have solved the problem by now. Yet, other users of similar hardware might be interested.)

[/SIZE]Telling from the symptom, a similar problem struck my Dell Latitude 6400,  Intel Mobile 4 Series Chipset Integrated Graphics Controller, during the first few weeks of running Ubuntu 12.04 32-bit, Unity Desktop.
I assume that one or two or more of the numerous update packages which Ubuntu kept on installing every other day may have improved the situation.
Yet, I am pretty sure that the one thing which made the problem disappear on this machine was adding the instruction ```
acpi_osi=Linux
``` to the commandline that launches the kernel.

How to do so?
```
sudo vi /etc/default/grub
``` Make sure the line about GRUB_CMDLINE_LINUX_DEFAULT reads ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
``` Tell Grub to use the modified setting for future reboots: ```
sudo update-grub
```HTH,
Karl
--
P.S.:
The solution that worked for my Dell Latitude E6400 having an internal Intel Mobility Graphics Card, was found in the German Ubuntu forum and is explicitly meant for Intel cards. It may not help with NVidia graphics cards.
By the way, my home desktop which has got an NVidia card and which runs Ubuntu 12.04 x64 plus Nvidia proprietary drivers has never exhibited any of the symptoms mentioned in this thread.

---

