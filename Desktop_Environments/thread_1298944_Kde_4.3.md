---
title: "Kde 4.3"
date: 2009-10-23
forum: Desktop Environments
---

### Post by renec2006 on 2009-10-23
I recently install KDE 4.3 on Ubuntu 9.04.
This environment runs super slow.
I have an Intel P Dual Core @ 1.46GHz.
I have 1GB of RAM running at 80%.
When running GNOME RAM is at 20%. Is it Xorg and plasma making my RAM go so high. If so, is KDE competing with MS on who can spike up a users RAM the highest? GNOME is really a good desktop. KDE is pretty, but... Is my solution to buy more RAM?

---

### Post by savagenator on 2009-10-23
Kde on ubuntu is kde not done right. I'm running kde on arch linux on my eee, and it runs fine at 160mb of RAM with chrome open and a barrage of activities to choose from.

On another note: keep in mind that your graphics drivers may be the cause. On my main machine with nvidia graphics, also running archlinux, kde slowly builds up my X ram usage to about 500 or 600mb of RAM, then I have to run a sudo /etc/rc.d/kdm restart

It's not you, it's your computer.

---

### Post by renec2006 on 2009-10-23
Think I'll stick with GNOME.

Thanks for your input..

---

### Post by lovinglinux on 2009-10-23
I have a P4 3.06 Ghz (single core) with 2 GB RAM and a nvidia 7300 GT.

I was able to run plasma desktop over Gnome in Ubuntu 9.04 without issues, plus compiz at full power and also screenlets. I'm not talking about running KDE or Gnome session. I'm talking about running plasma and gnome panel simultaneously, by launching plasma after logging into Gnome. So I doubt your problem it's KDE fault.

I'm currently running Karmic with standalone KDE 4.3.2 and the performance is excellent. I'm currently using 450 MB of RAM (20% of available memory) and Firefox alone is responsible for 140 MB (30 % of the total memory used). CPU usage is around 6 - 8%.

---

### Post by renec2006 on 2009-10-23
Hey! Here's something stupid I did and I hope nobody repeats what I just did. I removed all KDE programs under Package Manager. As soon as I hit 'Apply" i realized i have other applications that depend on some KDE apps.
WTF was i thinking!!!

---

