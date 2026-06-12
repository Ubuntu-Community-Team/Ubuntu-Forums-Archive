---
title: "Ubuntu Breezy always displays incorrect time"
date: 2005-12-20
forum: General Help
---

### Post by lazyfun on 2005-12-20
Hi everyone.  Breezy sets the wrong time for itself on every bootup.  I entered the correct time zone during installation.  If I manually change to the correct time via gnome it changes the system clock to the wrong time and windows gets it wrong (I dual boot).  I wish I could just stop it messing with the time on boot but I don't know how.  I've searched the forums - no luck.
Any help would be greatly appreciated :)

---

### Post by maglis on 2005-12-20
In dual boot (with windows) systems, M$ Windows change the hardware clock to local timezone. If you selected hardware time to be in UTC (GMT) when installing Ubuntu, then Ubuntu respects that and when it finds (after reboot ) the new-changed-by-windows time it assumes this is UTC and adjusts system clock to your local timezone. When you go and correct the time in Ubuntu, then Windows do not respect this change and changes it back to what it thinks is correct :evil:

What you should do is change Ubuntu to know that hardware time is not UTC but local and you'll have no more trouble after that.

---

### Post by maglis on 2005-12-20
Just to make it more clear. 

Linux has two clocks - one hardware, one software. Ubuntu keeps the hardware clock usually set to GMT and displays the correct local time in software by knowing the timezone. You can configure it to keep hardware and software clock both in local timezone.

1. Set you hardware (BIOS) clock to your local timezone correctly. Do this either in BIOS setup or just boot into windows....

2. reboot into ubuntu. Either play with command ***hwclock*** (man hwclock), or more simply repeat the time setup step you saw during ubuntu installation by running:
```
sudo base-config
```
You do not need to continue with the rest of base-config steps.

---

### Post by maglis on 2005-12-20
... and of course you can read the [fine HOWTO on time synchronization]("http://www.ubuntuforums.org/showthread.php?t=97041&highlight=hwclock").

---

### Post by lazyfun on 2005-12-20
Thanks a lot - that fixed it.  It was driving me nuts for ages!

---

### Post by Irony on 2005-12-20
Going to to the rcS file and changing it would also solve the problem:

*sudo gedit /etc/default/rcS*

Change;

[I]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/I]

to;

[I]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/I]

---

