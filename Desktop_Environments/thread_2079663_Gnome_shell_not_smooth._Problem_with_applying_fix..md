---
title: "Gnome shell not smooth. Problem with applying fix."
date: 2012-11-02
forum: Desktop Environments
---

### Post by Nekoshet on 2012-11-02
Hello. 
I recently installed my first linux system - ubuntu 12.04 LTS, and installed gnome-shell into it. But when i started using it, I noticed that the animation of the windows' movement are slow and not smooth. To be more specific, the situations in which the problem occurs are when I drag a windows across the screen, or when I press and unpress the Activities button.
I have an Intel e6600 cpu, 2 gigs of ddr3 Ram, and an ATI Radeon hd 4830 graphics card.
I started reading in forums about similar problems and i found a promising soulution - add the line "export CLUTTER_VBLANK=none" to the file /etc/environment. But when I tried to save the file after editing it, It didn't allow me. It didn't allow me to save the file.
I checked the file's properties in the "Permissions" section, and it says the owner of the file is "root", and I'm not allowed to change it.
Of course I was logged in to my account (the only account), and not to a guest account or something.
I'm new to linux and i don't understand how this stuff works.
How do I edit this line into the file and save it??
please help me.

---

### Post by Radwulf on 2012-11-08
In Linux the OS is controlled by root whereas users have limited access.  This means that by default user accounts have reduced ability to affect (and screw up) the OS; they are not like Windows administrative accounts.  In Ubuntu you can acquire limited root privileges through prefixing a command with sudo (for command line only) or gksudo (for a graphics interface) and then putting in your account password.  Thus to do what you want you can open a terminal and type:

gksudo gedit /etc/environment

Whereas gksudo gives you root (superuser) privileges, gedit is the program that lets you see the file, and /etc/environment is the file.  You should now be able to save.

---

