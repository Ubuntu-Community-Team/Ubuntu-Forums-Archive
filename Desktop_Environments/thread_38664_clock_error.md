---
title: "clock error"
date: 2005-06-01
forum: Desktop Environments
---

### Post by synaptic revolt on 2005-06-01
For some reason, my computer thinks it's in the UTC timezone, and it refuses to save my changes  :roll: 

It will be correct in the control panel, but won't change the clock in the tray, and if I leave the Date/Time screen and come back, it's back to UTC.


This happens even when I change it as sudo.


What happen

---

### Post by mstralka on 2005-06-01
I'm having the same problem.  It started after I sudo'd into kcontrol and checked the "automatically adjust time" box.  Then I unchecked it, changed the timezone from UDT to EDT and it didn't change the clock in the panel..

EDIT - found this thread which might help:
[http://ubuntuforums.org/showthread.php?t=29156&highlight=timezone](http://ubuntuforums.org/showthread.php?t=29156&highlight=timezone)

---

### Post by betrayed on 2005-06-01
I had the same problem.  I ended up using the gnome version of the same program to set the system time.  Quick reboot and everything was ok.

---

### Post by dstrebel on 2005-06-01
Run:
sudo tzconfig

It will prompt you if you want to change the timezone it will also display your correct timezone anyway so just change it anyways.
Follow the prompts to change timezone and it will fix the problem

also reboot so it sets the time to the hardware clock

---

### Post by Firetech on 2005-06-02
[QUOTE=dstrebel]also reboot so it sets the time to the hardware clock[/QUOTE]
 It is NOT needed to reboot! The system clock in Linux systems is independent of the hardware clock. It only uses it to set the system clock on boot, and save the time on shutdown. 
It will be correctly set when you reboot next time, and that is enough.
Rebooting is a WindowsCrazy Thing (r), and is mostly only needed on kernel panic and kernel changes.

---

### Post by synaptic revolt on 2005-06-02
[QUOTE=mstralka]I'm having the same problem.  It started after I sudo'd into kcontrol and checked the "automatically adjust time" box.  Then I unchecked it, changed the timezone from UDT to EDT and it didn't change the clock in the panel..

EDIT - found this thread which might help:
[http://ubuntuforums.org/showthread.php?t=29156&highlight=timezone](http://ubuntuforums.org/showthread.php?t=29156&highlight=timezone)[/QUOTE]

I saw that thread, and utc=no didn't help. Thanks though.

[QUOTE=dstrebel]Run:
sudo tzconfig

It will prompt you if you want to change the timezone it will also display your correct timezone anyway so just change it anyways.
Follow the prompts to change timezone and it will fix the problem

also reboot so it sets the time to the hardware clock[/QUOTE]

tzconfig thinks I'm in the correct timezone already, but I went through and "changed" it anyway, and now it works.  :smile: 

Thank you!

---

