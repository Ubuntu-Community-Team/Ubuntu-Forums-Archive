---
title: "Gnome Desktop Is Gnome!!! (Terminal Only) Need Help!!!"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Robroy11976 on 2005-12-03
Hi, need help on my ubuntu 5.04 .... I was using ubuntu 5.04 for over a week now ... when suddenly i installed some update which were prompting in the panel system tray to install.  I think there was 2 broken link after that in the synaptic package manager, i think it was python2.3-gtk2 and another one.  I tried to re-install it but error occurs when i do so.  So i decided to uninstall those 2 package.  After reboot, it won't start at the desktop screen ... what i does is only loading to the terminal command.  What happened to my desktop?? How could i bring it back???

     I tried using all commands like "sudo apt-get -f install", "sudo apt-get dist-upgrade","sudo apt-get upgrade", but it won't fix the prob ... Need help on bringing back my ubuntu desktop screen ....

---

### Post by teaker1s on 2005-12-03
hit escape at boot 
grub screen boot a previous kernel
if it boots okay your need to install linux-restricted-modules  for the latest kernel
with synaptic

failing that

sudo apt-get ubuntu-desktop

then 
sudo dpkg-reconfigure xserver-xorg 


post your results and either myself or someone else will try to suggest a solution if we have more ideas

---

### Post by Robroy11976 on 2005-12-03
Ok thanks .. i'll try it out ... Hopefully it will ok ... :)

---

