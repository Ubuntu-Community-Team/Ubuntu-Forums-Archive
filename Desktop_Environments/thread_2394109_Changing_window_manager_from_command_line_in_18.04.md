---
title: "Changing window manager from command line in 18.04?"
date: 2018-06-12
forum: Desktop Environments
---

### Post by dbsoundman on 2018-06-12
Hi all, I've found lots of outdated threads on this topic, but nothing that seems to be relevant to Ubuntu 18.04 LTS. Here's my situation: I would like to disable the default graphical login screen and have my machine go directly to a shell for user login, then manually run "startx" afterward to start the desktop environment. However, I also want to experiment with different window managers: right now I have the stock Ubuntu GDM3, as well as Openbox and i3wm. What I would like to do is be able to run some sort of command after I log in at the terminal prompt to set the desired window manager, THEN launch X via startx.

The reason I want to disable the graphical login is because of existing issues with my laptops graphics and the latest Linux kernel, which I don't believe will be resolved soon, and I don't really care to fiddle with. :)

Let me know what you think, thanks!

---

### Post by ajgreeny on 2018-06-12
I think you are a little confused about "window managers" and "display managers" which are not quite the same thing.

GDM3 is a display manager and a display manager is not absolutely necessary for a Linux distro, even one using a GUI desktop, as it is possible to start the GUI from command line after logging in.
Openbox and i3wm along with such things as compiz, mutter, etc etc are window managers, and I believe one of those is essential if you wish to run a windowed GUI DE.

For more info and possible ideas see
[https://askubuntu.com/questions/882422/how-can-i-disable-all-display-managers](https://askubuntu.com/questions/882422/how-can-i-disable-all-display-managers)
[https://askubuntu.com/questions/800239/how-to-disable-lightdmdisplay-manager-on-ubuntu-16-0-4-lts](https://askubuntu.com/questions/800239/how-to-disable-lightdmdisplay-manager-on-ubuntu-16-0-4-lts)
[https://askubuntu.com/questions/829108/what-is-gdm3-kdm-lightdm-how-to-install-and-remove-them/829110](https://askubuntu.com/questions/829108/what-is-gdm3-kdm-lightdm-how-to-install-and-remove-them/829110)

---

### Post by dbsoundman on 2018-06-12
Excellent info; I definitely mixed up the window manager vs. display manager there...

My display manager is gdm3, and I would like to disable it and use a text-only login screen; I would then like to know how I can launch openbox, i3wm, etc. from the command line. I looked at the links in the previous post, but I wasn't sure if I would then want to issue a "startx" then "sudo systemctl start <window manager of choice>", or would I only do the systemctl command, or ?

---

### Post by tomachi on 2019-03-26
Edit grub bootloader to disable GUI at startup. From the local terminal try:

startx

via ssh -Y user@box you could try:
xcalc
openbox
dolphin
plasma

---

