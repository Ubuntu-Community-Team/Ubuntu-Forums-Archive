---
title: "Display Problems (1024*768 - Can not get 1280*1024) nVidia GF FX5200"
date: 2006-01-10
forum: Desktop Environments
---

### Post by SamTheMan on 2006-01-10
Hi,

I installed Ubuntu Linux yesterday, however, I'm having a problem. My monitor doesn't display resolution properly if the computer/in isn't set to use 1280*1024. At the moment I'm using half of my monitor on Ubuntu. I have checked the settings and I have noticed that it wont let me have the resolution above 1024*768. I checked the IRC channel to look for help, it was way to crowded to talk to anybody really. I do remember somebody saying install the Restricted Kernel Modules, can anybody explain this or help me fix my problem in any way?

-- I'm in a rush too so if I am the wrong forum, please don't be abusive, just point me in the right direction.

Thankyou in advance for any help I recieve. 

Sam.

---

### Post by Ampersand on 2006-01-10
In Synaptic, get the linux-restricted-modules package for whatever version of the kernel you're using, and nvidia-glx. Once those have installed, open a terminal and run
```
sudo nvidia-glx-config enable
```
and then
```
sudo /etc/init.d/gdm restart
```
This will log you out, so save anything unsaved first. 

You should then see the NVidia logo, and be logged in. If you don't, log in at the prompt that should appear and run
```
sudo nvidia-glx-config disable
```
to restore your previous settings.

If it works, you should be able to run
```
sudo dpkg-reconfigure xserver-xorg
``` 
and select a higher resolution. Make sure you select the nvidia driver at this point.

---

### Post by SamTheMan on 2006-01-10
edit:

Where do I get the Linux Restricted Modules package from?

- Don't worry, found Synaptics, looking for the right files, although I don't know exactly what I'm looking for...

---

### Post by lisje on 2006-01-10
I don't think you need those "linux restricted modules"package... but you just need to edit your xorg.conf 
```
sudo gedit /etc/X11/xorg.conf
```

and edit the Section "Screen" to your needs.
here is mine (yes my current card is an ati but it makes no difference): 
```
Section "Screen"
	Identifier	"Dell Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf) 2"
	Monitor		"Dell Scherm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
       ...
```

if you use the nvidia driver you should enter "nvidia" as driver in your Section "Device", like this:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```
otherwise your driver is probably just nv .. so leave it like it is.

save the file en restart X by pressing Ctrl+Alt+BackSpace. (or any other method you know).. don't forget to backup your xorg.conf before you edit it!!!!
So you can put the old configuration back :D 

Hope it helps!
greets,
Lisje

---

