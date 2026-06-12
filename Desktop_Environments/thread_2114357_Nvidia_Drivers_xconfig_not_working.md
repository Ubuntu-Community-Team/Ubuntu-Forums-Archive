---
title: "Nvidia Drivers xconfig not working"
date: 2013-02-09
forum: Desktop Environments
---

### Post by Mikelmaotje on 2013-02-09
Hello ubuntu community!

I have googled this for a couple of hours and i can't find the solution.

I am trying to configure my nvidia card setting so i run nvidia-settings to pop-up the interface but once i run it a message box appears saying i need to run nvidia-xconfig. But if i open the terminal and try to run the command nothing happens.

After googling for a little while i found out that i should try running "/usr/lib/nvidia-current/bin/nvidia-xconfig" and that created the config file but now it will only get the 640x480 resolution for my primary display (laptop screen) but it does get all the resolutions for my secondary screen..

How can i get my resulution back and fix the xconfig? Im not very experienced yet with linux so if you need some debug information i would appriciate an explination to why that would help for future purposes, thanks :)!

Im running:
Ubuntu 12.10 64bit with gnome 3
I have nVidia GeForce 540M

Edit:
I removed the xorg file for to re-create the file with default settings which sets my resolution back to normal but still doesnt allow me to view all the nvidia-settings options

---

