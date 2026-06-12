---
title: "ubuntu + RAM"
date: 2005-07-10
forum: Desktop Environments
---

### Post by lukus001 on 2005-07-10
ubuntu only registers 885mb of RAM on my system when i have 2GB (both working because their the type with LEDs on them)

It used to say the correct 2024mb or what ever it is... i think it was a new update to ubuntu and then i started noticing the wrong ammount....   Hould i be worried that it's not going to be using my RAM properly, or just a "system moniter" glitch?

Cheers

---

### Post by codejunkie on 2005-07-10
open the terminal and type uname -r if it says something like 2.6.10-5-386 thats the problem the 386 kernel doesn't support large amounts of ram it only see's a part of it  so you need to upgrade your kernel.

---

### Post by lukus001 on 2005-07-11
Yeah, uname -r returns "2.6.10-5-386"

How do i go abouts changing it /upgrading the kernal?

---

### Post by McPringle on 2005-07-11
[QUOTE=lukus001]Yeah, uname -r returns "2.6.10-5-386"

How do i go abouts changing it /upgrading the kernal?[/QUOTE]

Use synaptic for it. After rebooting you can choose between the already installed 386 kernel and your newly installed kernel. If the newly installed kernel works well, you can remove the 386 kernel with synaptic.

hth
McPringle

---

### Post by Leif on 2005-07-11
Depending on your CPU, you want to install linux-k7 (for athlons), linux-686-smp (for P4's with hyperthreading) etc.

---

### Post by Morimando on 2005-07-11
[QUOTE=Leif]Depending on your CPU, you want to install linux-k7 (for athlons), linux-686-smp (for P4's with hyperthreading) etc.[/QUOTE]
thanks ^^ i just realized i had the same problem  ;-)

---

### Post by lukus001 on 2005-07-12
[QUOTE=McPringle]Use synaptic for it. After rebooting you can choose between the already installed 386 kernel and your newly installed kernel. If the newly installed kernel works well, you can remove the 386 kernel with synaptic.

hth
McPringle[/QUOTE]
Well i've installed one and i never got to pick which one i want to use, i keep gettting some error about it failing.... X server that is... sauing its possible it hasnt been configured properly...

How do i fix that now -.- im forced to consol mode cant open synaptic etc.. lol

---

### Post by Morimando on 2005-07-12
[QUOTE=lukus001]Well i've installed one and i never got to pick which one i want to use, i keep gettting some error about it failing.... X server that is... sauing its possible it hasnt been configured properly...

How do i fix that now -.- im forced to consol mode cant open synaptic etc.. lol[/QUOTE]
Well you need linux-2.6.10-7-k7-restricted-modules also...guess nvdidia has to be reinstalled due to the change of kernel

---

### Post by lukus001 on 2005-07-12
well i'm getting nvidia errors... so i expect it is nvidia..> Fatal: module Nvida not found
Faiuled to load the nvidia kernal module!
screens found but non have a usable configuration

fatal error, no screens found

i tried re installing by sudo apt-get install nvidia-glx + nvidia-serttings but it says i have the latest version so im gessing i have to remove it then re-install it? which i dont know how -.-

linux-2.6.10-7-k7 doesnt seam to exist for installtion?

---

### Post by codejunkie on 2005-07-12
if you cant get into X at all, at the failsafe terminal type 
```
sudo nano /etc/X11/xorg.conf
``` find this section
```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```
and replace "nvidia" with "nv" or "vesa" save and restart this will get your default X session up and running so you can reinstall the nvidia drivers.
Edit: you can also install the linux-restricted modules for the k7 kernel from the terminal with this
```
sudo apt-get install linux-restricted-modules-k7
```

---

### Post by lukus001 on 2005-07-12
```
sudo apt-get install linux-restricted-modules-k7
```

yeppie <3

works now... what did i d wrong then? forget to install that i supose? -.- or install the wrong file in the first place lol

---

