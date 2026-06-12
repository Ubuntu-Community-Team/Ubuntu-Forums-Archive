---
title: "Help - No display after gdm-2.20 installation"
date: 2010-03-01
forum: Desktop Environments
---

### Post by Lektorvis on 2010-03-01
Hi

In order to get a new theme running on my Karmic I
ran the following code in the terminal:
sudo apt-get install gdm-2.20
I selected the gdm-2.20 as standard when prompted.
But after rebooting Ubuntu halted after the splash screen, only showing a black screen. 

Please how can I recover from here?

---

### Post by Lektorvis on 2010-03-01
Hurray I'm back with Gnome display again

This is how I managed to do so - by my best memory -
1- On reboot I helt shift down in order to reach Grub.
2- In Grub I selected 'recovery mode' 
 - and on the next screen 'netroot'
3- At the terminal-prompt I entered:
   sudo apt-get install gdm
4- Gdm-2.20 then was overwritten with gdm 'zero'
 - When prompted with the blue screen this time I selected 'gdm' as default.
On the next reboot everything was back as normal:)

---

