---
title: "Xubuntu 18.04 boots to blank screen"
date: 2020-07-09
forum: Desktop Environments
---

### Post by twgray on 2020-07-09
I have an Intel processor on an Asus motherboard with an Nvidia GeForce GTX 1060 6GB video card, running Xubuntu 18.04 with latest updates (waiting for 20.04.1 release later this month for LTS upgrade).

My rather interesting problem is, after the login screen, Xubuntu presents a blank screen.  If I then go to a tty terminal, via Ctrl-Alt-F1-F6 and wait for the cli login prompt (I don't have to login) and then press Ctrl-Alt-F7 I get my graphical desktop screen.  This is the only way to get to the GUI.

I have tried "sudo service lightdm reconfigure" to no avail.  I thought about reinstalling the Xubuntu desktop, but Xubuntu doesn't appear to have the actual "Xubuntu-desktop" package installed, apparently using only some subset.  I'm not sure which package[s] to install to re-install, reconfigure, and possibly fix whatever is broken.  

I could try "sudo apt install Xubuntu-desktop no-install-recommended" but I'm unsure about whether this will break more than it fixes.

Any suggestions would be appreciated!

---

### Post by geofftf on 2020-09-07
What happens when you run Xubuntu from a live USB or DVD? Do you have the same problem? If not, I would suggest reinstalling Xubuntu.

---

