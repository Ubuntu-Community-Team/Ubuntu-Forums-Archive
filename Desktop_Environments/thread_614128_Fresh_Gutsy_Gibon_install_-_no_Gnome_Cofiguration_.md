---
title: "Fresh Gutsy Gibon install - no Gnome Cofiguration Editor"
date: 2007-11-15
forum: Desktop Environments
---

### Post by zee on 2007-11-15
Hi all.
  I just installed a fresh copy of Gutsy Gibon only to find there is no Gnome Configuration Editor (the thing under Applications->System tools). I also found out there are no icons for Gkrellm I installed as well. Where are they?

  I have also a second question: why aren't any of the commands in /etc/rc.local parsed ? The commands I would like to be parsed are:
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
echo conservative > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor 

Thanks in advance,
zee

---

### Post by jpietari on 2007-11-17
By default, I don't think the gnome configuration editor is shown in the application menu.  I had to go into "edit menus" and turn it on.

---

