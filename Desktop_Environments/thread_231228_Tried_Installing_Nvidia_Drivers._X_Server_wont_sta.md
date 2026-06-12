---
title: "Tried Installing Nvidia Drivers. X Server wont start!"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Royal2000H on 2006-08-07
OK, so first off, im on Dapper, with an Nvidia GeForce 4 MX 440.

I see the display fine.
But I'm about to install Enemy Territory using this guide [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

so I go to the BinaryDriverHowto/Nvidia like the guide says

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I install nvidia-glx + nvidia-glx-dev

I search the restricted modules, and see it's already installed

In terminal I do sudo nvidia-glx-config enable

It says something about file changed, so I do the update MD5 like it instructs me to

I re-run sudo nvidia-glx-config enable

I restart X Server with Ctrl-Alt-Backspace

And I get "Failed To Start X Server" would you like to view <whatever it said>

EDIT!:
Sorry, read the troubleshoot, that fixed it.... sorry for the trouble.
Mods: please delete,

---

### Post by Scythe!? on 2006-08-07
I had the very same problem. To make a backup of the xorg.conf file before you do a driver update or anything type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will return it to a working state if the driver fails

To recover from it type in the text console:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
then type **sudo reboot** to reboot the system.#

I tried many methods and it always ended up like yours. Failed to start X server. I tried using Automatix and its fine now and nvidia driver is installed. Try it and see if it works for you.

EDIT: Just seen your edit note. Woops lol

---

