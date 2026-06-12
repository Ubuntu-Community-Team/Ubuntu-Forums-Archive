---
title: "xfce Question"
date: 2010-07-07
forum: Desktop Environments
---

### Post by KdotJ on 2010-07-07
I have Ubuntu 10.04 installed on my netbook, and recently I have really started to love Xfce. I had xubuntu running in a VM to see how it was, and I liked the desktop and the great customisation. I installed xfce on my netbook via Synaptic, along with many, many other packages and add ons for it. However, in an xfce session, it in still not the same as it is on xubuntu.

For example: 
- Some of the available panel items are missing, despite me installing the xfce-goodies package and others.
- Some of the panel icons are still the ubuntu colours despite me installing the themes package etc.
- The xfce menu in the main panel has a different layout to that of xubuntu, and from what I have read is a bit long winded to edit. Not that I have a problem with doing so, it's just a bit long.

My question is, can I have my xfce set up so it is exactly that of xubuntu? I have installed xubuntu-desktop meta package from synaptic but still no luck. It is a bit of hassle for me to install xubuntu instead, but is this my best bet?

Thank in advance for any help.

---

### Post by Brandon Williams on 2010-07-08
Installing xubuntu-desktop means that you've got all the packages installed that you need. In order to start from the standard xubuntu configuration settings, you will need to reinitialize your xfce config. The easiest way to do this is to 1) log out from your GUI session, 2) log in to a console session (press Ctrl+F1 to get to a console login prompt; Ctrl+F7 to get back to a GUI login), and 3) run 'rm -Rf ~/.dmrc ~/.cache ~/.config ~/.gconf ~/.gconfd ~/.gnome2 ~/.gnome2_private ~/.icons ~/.local'. The list of directories in that command line should cover all the directories that contain high-level GUI configuration files, and deleting all of them will mean that you start from zero the next time you log in. It may be enough to delete just the ~/.config directory, but I would delete all of them to have the greatest chance of resolution on the first attempt.

---

### Post by KdotJ on 2010-07-08
Thanks for the reply, I'll give this a go

---

### Post by KdotJ on 2010-07-08
Turns out it was even easier than that, all I had to do was select "Xubuntu Session" at the gdm, before I had it set on "Xfce Session"

All is good now :D

---

