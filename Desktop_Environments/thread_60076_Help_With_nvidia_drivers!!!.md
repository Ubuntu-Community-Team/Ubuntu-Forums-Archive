---
title: "Help With nvidia drivers!!!"
date: 2005-08-26
forum: Desktop Environments
---

### Post by Pota_BGW on 2005-08-26
I was install the driver for nvidia, and when I reboot computer there is only one display on my tv! How can I back display on monitor?

Thank you, Pota

---

### Post by KingBahamut on 2005-08-26
sudo nvidia-glx-config enable 

did you install the drivers from synaptic/apt-get , or did you try to compile the drivers supplied by nvidia's site?

---

### Post by Pota_BGW on 2005-08-26
I did this

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

---

### Post by happogiri on 2005-08-26
My problem is: I did exactly like in every HOWTO in this forum, every time with fresh install on Ubuntu 5.04 and all the time result was that when I start the 'gdm' again, I end up staring blank screen (black, no signal). I can login (I know this from the sounds :) ), and when I come back to terminalscreen (ctrl+alt+F1) i can see that 'gdm' has started, just no visual components of its existence can be seen.

For two days, about 12 hours a day I've been trying to do this...  ](*,)

---

