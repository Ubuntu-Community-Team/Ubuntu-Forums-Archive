---
title: "Very big problem with the Gnome-panel - PLEASE HELP!"
date: 2007-09-24
forum: Desktop Environments
---

### Post by Hashte on 2007-09-24
My problem is a very frustrating one:

Gnome-panel crashes randomly just after entering Gnome (even in failsafe mode). Like 3 times in 4 logins. I must reboot and enter another way in Gnome (through X-Client Script, Gnome or Gnome Failsafe). System tray still works, but the rest freezes.

Every time gnome panel is likely to crash just after entering gnome, i hear no sound when clicking on a panel icon (normally I have). The first pressing on a button works good, but by the second one it crashes.

Most of the time, after the crash, I can open only programs using katapult. And I can actually open only KDE programs, any other Gnome program crashing (e.g. I can open Konsole, but not Terminal).

I realised that it happens mostly after I've cold booted the system (thus not after a previous reboot, but after I powered on the laptop). And most of the time, if it finally works, I can log in and out or I can reboot the system as many times as I want.

Also, after the crash, if I reset the X-server and I log in into KDE, all the Gnome-programs will not work. I've tried to kill the gnome-panel, but I can't reopen it.

Can anybody help me? Does anyone know what the problem should be or what should I do to get this working?

Thank you very much in advance!

---

### Post by jnorthr on 2007-09-24
Yes, it must be frustrating. Is there any way you can re-install gnome as it sounds like a corruption issue that could be corrected (possibly) with a fresh copy of that package. If kde runs ok but gnome does not, then what else could it be ?

---

### Post by neaeo on 2007-09-24
If you have applets in the panel, I would suggest to remove them one by one to see if it's related to an applet.

---

### Post by raul_ on 2007-09-24
Try moving the .gnome folder to another place, and then delete it from the home folder. You'll lose your configuration but maybe it's a corrupted profile

---

### Post by Hashte on 2007-09-25
I have reinstalled most of the relevant packages that have gnome in their name. It worked quite good since yesterday till now (5 or 6 times booted up my laptop) and all went fine.

BUT NOW, it's back again ](*,). I don't know what to do further :-(

I have a feeling that it has something to do with my wireless router. Otherwise there's no other reason to freeze in such a random way. What can I do ?

If somebody has any other idea, please let me know!

P.S. How can I re-install Gnome as a whole? I have personally the ubuntu-desktop package deselected in Synaptic:confused:. I don't want to reinstall it this way because it will reinstall the old compiz...I have manually installed the new one, so I don't want to overwrite it:(.

---

### Post by Lacrimstein on 2007-09-25
Reinstalling packages isn't enough - all the configuration files are still there on your hard drive. try the "remove completely" option in synaptic

---

### Post by Lacrimstein on 2007-09-25
I hope this isn't too late, but I forgot to tell you that by completely removing gnome-panel, it   is quite possible that the entire ubuntu-desktop will be removed, and all you will be left with is the command line.

---

### Post by Hashte on 2007-09-26
10x for your replies guys! But it just doesn't work :( Anyway...I'll stick to KDE the next 3 weeks, till the official release of Gutsy (18th October I think). I'll try to make also a backtrace of the bug and submit it to Launchpad.net.

---

