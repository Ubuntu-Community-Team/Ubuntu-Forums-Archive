---
title: "Gnome freezes on login"
date: 2006-05-16
forum: Desktop Environments
---

### Post by pjeeanah on 2006-05-16
Hi all

I am a fedora user but wanted to try Ubuntu 5.10. Basic installation went fine. However on first boot, the machine did not go further than hotplug. 

After some googling, I managed to disable hotplug. 

This time the installation went fine and I managed to get on to the login manager.

 However when I login, only the mouse pointer appears in a brown background and the machine hangs. 

Ctrl+Alt+F1 does not work and I have to hard reset the machine. My .xsession_errors file shows some problem loading Esound.

I have a realtek hd audio sound controller with an intel ICH7 chipset. 

My vga card is PCIEx NVIDIA 6600 LE.

How can I prevent gnome from loading sound so that I can login in the gui.


lspci does not appear to have detected the integrated sound controller.


Any help would be greatly appreciated.


By the way, everything works fine with FC5.


PS I managed to get hotplug running by putting the module snd-hda-intel in the blacklist.

---

