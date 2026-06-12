---
title: "Login Problems"
date: 2006-09-23
forum: Desktop Environments
---

### Post by intelliprompt on 2006-09-23
I'm a new player in the Linux game, so I'm sorry if I sound at all like an idiot here, but I've been having trouble with the login of Ubuntu Linux. I have a dual boot system and am trying to get Linux configured enough so I can use it as my primary OS, but today when I logged on to make some changes the screen changed from the login to a blank (appeared to be a command terminal) screen displaying two lines which were:

Ubuntu 6.06.1 LTS intelliprompt-comp tty1
intelliprompt-comp login:

This message is displayed for less than a second I'd say (I had to go through the problem a few times to figure out what it said) and then goes back to the login screen asking for my username. I tried typing my login on the command terminal-esque screen, but it flashes back to the login far too quickly.

Also, I noticed today that I have two more options for which OS I want to select during the boot that weren't there before. Both options seem to be copies of existing ones.

Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernal 2.6.15-27-386 (recovery mode)

Those are both listed two times, and it wasn't like that before today. I'm not sure if it matters at all, or if its even related to my login problem, I just noticed that both of the occurances happen to coincide chronologically.

---

### Post by kidcharles on 2006-09-23
I can definitely help you with the multiple Ubuntu entries in Grub. You probably did an automatic update, which added a newer version of the linux kernel. Ubuntu keeps the old kernels around, and leaves the option in the Grub boot menu. If you look closely at the entries, I'll bet you'll see a difference in the version number (probably something like 2.6.15-26 and 2.6.15-27), these are different kernels. You can change whether or not old (or new) kernels show up in the grub boot menu by editing /boot/grub/menu.lst by 'commenting out' (adding #'s) to the entries you do not want to see.

As for your login issue, it smells to me like a problem with x.org, the graphical environment. If you do indeed have different kernel options at boot, try a different one and see if the problem persists.

---

### Post by intelliprompt on 2006-09-26
According to GRUB, both kernels are the same version, and I cant get past the login screen, so I dont know how to fix anything. I'm going to be reinstalling Linux onto a different HD soon, so I'll just wait and hope that I don't get the same problems on that install.

---

