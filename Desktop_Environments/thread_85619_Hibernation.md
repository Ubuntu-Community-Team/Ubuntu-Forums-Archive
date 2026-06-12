---
title: "Hibernation"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Beta-Glitch on 2005-11-03
First off, congrats! kubuntu is the first distro to run ACPI out of the box, and resume from hibernation without a screen of garbage on my IBM R40e laptop!

the only problem with this ideal scenario is that after it's come out of hibernation, the mouse no longer works. The KB works fine and the machine responds without problem, but the mouse doesn't work at all (not even a mouse button). Can you offer any assistance, or am I still waiting for full hibernation support?

also, a small note, any one know if it's possible to use the SyncML client Bluetooth profile on my Nokia 6680 to syncronise to Kontact/Evoluntion?

Many thanks

---

### Post by wrtrdood on 2005-11-04
I have a problem with that as well.  Fortunately on my laptop (Fuji P1120) I have a function key that lets me disable then re-enable the stick mouse.  I discovered some time ago that it seems to be something with psmouse.  If you don't have the function key option, try opening a terminal window and unload then reload psmouse:

sudo rmmod psmouse
sudo modprobe psmouse

Good luck.

---

### Post by Beta-Glitch on 2005-11-05
that works brlliantly!

now..is there a way to set the machine to do those commands stright after resuming from hibernation?

---

### Post by arthur_kalm on 2005-11-05
Hi, I'm actually wondering how you add a hibernate option to your logout menu? I know that Ubuntu has the option, but how do I add it to my KDE menu?

Thanks.

---

### Post by wrtrdood on 2005-11-10
[QUOTE=arthur_kalm]Hi, I'm actually wondering how you add a hibernate option to your logout menu? I know that Ubuntu has the option, but how do I add it to my KDE menu?

Thanks.[/QUOTE]


Once configured, I believe that klaptop allows this (can't verify since I'm not using my Linux box right now).  It's not on the actual KDE logout dialog.

---

