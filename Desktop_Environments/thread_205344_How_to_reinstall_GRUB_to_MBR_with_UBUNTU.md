---
title: "How to reinstall GRUB to MBR with UBUNTU"
date: 2006-06-28
forum: Desktop Environments
---

### Post by kazuya on 2006-06-28
If I have windows XP, then I install Ubuntu to dual boot, but later on through reinstalling windows , I mess up the grub install on MBR, can I easily repair or restore my GRUB on MBR?

How do I do so using just the Ubuntu ISO CD?

Any ideas?

With Mepis, you simply boot to CD and do a reinstall GRUB to MBR, and it is finished.

Is there such an option in Ubuntu?

---

### Post by bartbes on 2006-06-28
well you first have to start the installation and as soon as you can go further to GRUB installation ( don't remember how exactly but I think there was a menu when you pressed back ), but when I did that (I tried to install LILO then, which failed) it asked me to go through the partitioning process ( set the root partition as / and it's ok ).

---

### Post by ajgreeny on 2006-06-28
Another way if you have a floppy drive;  put grub there before reinstalling windows with:-
sudo grub-install /dev/fd0
If you get an error message about no bios entry, just add:-
(fd0)  /dev/fd0
to the bottom of your /boot/grub/device.map file and try again.

Then after windows has restored your MBR, you can get to Ubuntu with the floppy and then reinstall grub with:-
sudo grub-install /dev/hda
(This assumes hda is where your windows is, so change that if needed.)
Good luck.

---

