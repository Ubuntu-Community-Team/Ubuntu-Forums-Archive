---
title: "Change Display Manager"
date: 2010-03-04
forum: Desktop Environments
---

### Post by xarhelios on 2010-03-04
SO I had a nice setup of gNewSense , an ubuntu based distro with only FOSS repos, in a vbox vm on win7 host and I installed KDE4 on it to see how it was progressing. upon doing this, I set KDM as my default display Manager. When I reboot to see if it worked, I get a the normal list of daemons and stuff starting up, and I see

K Display manger not starting, not default
GNOME Display manager not starting, not default
starting Virtualbox Guest additions

then it stays there, as VBox additions require X. 

When I boot into a LiveCD in order to change /etc/X11/default-display-manager to /usr/lib/gdm, I reboot and get the same thing. This leads me to believe that gNewSense, and possibly ubuntu, use the inittab method, which I cant change unless I have GRUB installed, Right? well, the problem here is that I imaged the install from another machine and GRUB didn't get copied over, so I use supergrubdisk to boot into a distro. This has never been a problem until now. 

Are there any other files I can edit to change default display manager? If not, how can I boot into the console and reconfigure the display manager properly?

---

