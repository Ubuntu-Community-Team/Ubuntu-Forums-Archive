---
title: "Auto logout from Xsession using Xming"
date: 2011-05-16
forum: Desktop Environments
---

### Post by j123123 on 2011-05-16
I have one Ubuntu 11.04 PC and one WinXP PC, and I use Xming 6.9.0.31 with XDMCP to connect to Ubuntu. It is working fine without any problem, the only issue is: if I leave it idle(or backgroud processes) for 2 hours, the X session will auto log me out and kill all my build processes. I almost can't do any night build within Xming's Xsession. Can anyone here help me out? Thanks in advance.

By the way, I've disabled all screensaver related stuff, even tried delete /usr/bin/gnome-screensaver, no help.

---

### Post by wildmanne39 on 2011-05-16
> **j123123 said:**
> I have one Ubuntu 11.04 PC and one WinXP PC, and I use Xming 6.9.0.31 with XDMCP to connect to Ubuntu. It is working fine without any problem, the only issue is: if I leave it idle(or backgroud processes) for 2 hours, the X session will auto log me out and kill all my build processes. I almost can't do any night build within Xming's Xsession. Can anyone here help me out? Thanks in advance.

By the way, I've disabled all screensaver related stuff, even tried delete /usr/bin/gnome-screensaver, no help.
Hi, did you also go into power management while in the screensaver window?:D

---

### Post by j123123 on 2011-05-16
> **wildmanne39 said:**
> Hi, did you also go into power management while in the screensaver window?:D
 
I've set both Actions & Display to Never in Power Management Preferences's "On AC Power" tab, no help.

---

### Post by wildmanne39 on 2011-05-17
> **j123123 said:**
> I've set both Actions & Display to Never in Power Management Preferences's "On AC Power" tab, no help.
Hi, for some reason it is not saving your configuration setting is what it sounds like to me, I will look in my book and see if I can find an answer, but it makes it harder with natty not all the commands in my book that is only 2 years old work.:)

---

### Post by wildmanne39 on 2011-05-17
> **j123123 said:**
> I've set both Actions & Display to Never in Power Management Preferences's "On AC Power" tab, no help.

Hi, this should work. Put this command in terminal.
gksu gedit /etc/hdparm.conf
under spin down check #spindown_time = 24, see what it is set at. If what you see is exactly what I have it should not put your hard drive to sleep, if the dollar sign is missing in front of spindown_time add it and that should stop the problem.:D

---

### Post by j123123 on 2011-05-17
> **wildmanne39 said:**
> Hi, this should work. Put this command in terminal.
gksu gedit /etc/hdparm.conf
under spin down check #spindown_time = 24, see what it is set at. If what you see is exactly what I have it should not put your hard drive to sleep, if the dollar sign is missing in front of spindown_time add it and that should stop the problem.:D
 
Here is what I saw in /etc/hdparm.conf:
...
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
...
 
Pls let me know what you want to modify.
 
BTW, the auto logout only happens to my Xming Xsession, the Ubuntu PC is still running(not in sleep/hibernation mode), I can still telnet to do anything, and the rest of background processes are still running.

---

### Post by wildmanne39 on 2011-05-17
> **j123123 said:**
> Here is what I saw in /etc/hdparm.conf:
...
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
...
 
Pls let me know what you want to modify.
 
BTW, the auto logout only happens to my Xming Xsession, the Ubuntu PC is still running(not in sleep/hibernation mode), I can still telnet to do anything, and the rest of background processes are still running.
Hi, I am out of advice. Maybe some with more experience can help.

---

### Post by wildmanne39 on 2011-05-17
> **j123123 said:**
> Here is what I saw in /etc/hdparm.conf:
...
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
...
 
Pls let me know what you want to modify.
 
BTW, the auto logout only happens to my Xming Xsession, the Ubuntu PC is still running(not in sleep/hibernation mode), I can still telnet to do anything, and the rest of background processes are still running.

Bump

---

### Post by j123123 on 2011-05-18
Up ..................

---

