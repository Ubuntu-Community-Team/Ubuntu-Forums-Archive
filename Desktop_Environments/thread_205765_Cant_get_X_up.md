---
title: "Cant get X up"
date: 2006-06-28
forum: Desktop Environments
---

### Post by FazeX on 2006-06-28
I have just recently switched to Linux and having trouble getting started.
When I first installed Kunbuntu it would go through the startup and freeze 
with a blinking cursor. So i changed my xorg.conf for vga and now it still
doesnt load X but takes me to the console instead of freezing.

xorg.conf
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"vga"
	BusID		"PCI:4:0:0"
EndSection

AMD64 3500
Nforce Motherboard
2x6600GT SLI Video
1G Ram

Please help me so I dont have to go back to Windows :(

---

### Post by trent dillman on 2006-06-28
Instead of 'vga' try 'vesa'.

---

### Post by johnc4510 on 2006-06-28
It looks like you have the wrong driver. Were it says vga, it should say nvidia.
At the console, type these commands in:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
Then reboot
I think this will do it.

---

### Post by tseliot on 2006-06-29
[QUOTE=johnc4510]It looks like you have the wrong driver. Were it says vga, it should say nvidia.
At the console, type these commands in:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
Then reboot
I think this will do it.[/QUOTE]
"sudo nvidia-glx-config enable" is broken. Please try "sudo nvidia-xconfig" instead.

And if your computer freezes try point 4 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

