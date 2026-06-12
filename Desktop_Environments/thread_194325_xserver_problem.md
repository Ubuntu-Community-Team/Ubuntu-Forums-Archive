---
title: "xserver problem"
date: 2006-06-11
forum: Desktop Environments
---

### Post by joriad on 2006-06-11
Last week I made the change from windows to Ubuntu 5.10. So as you can see I am very new to all this. I then downloaded and installed Automatix 6.1-6, which seemed to go fine until I restarted my computer and then I got a failure message: 

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?" 

some of the readout goes as follows

(EE) GartInit: unable to open /dev/agpgart (no such file or directory)
(EE) I810 (0): Agp Gart support is not available. Make sure your kernel has agpgart support or that the agpgart kernel module is loaded. 
(EE screen(s) found, but none have a usable configuration. 

Fatal Server Error:
no screens found

I tried sudo dpkg-reconfigure-xserver-xorg but it did not resolve the problem. I then posted in the automatix area and was given this information:


enter code sudo vi /etc/X11/xorg.conf

Code:
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
End Section

then change "i810"? to read "vesa" in the vi editor then enter :wq to save

Well the main problem of xserver not starting still persists, however it has changed the problem from GartInit and I810 to a mouse problem which is keeping the gui from starting. Now I get these errors:

(EE) xf86OpenSerial: cannot open device /dev/input/mice
(EE) configured mouse: cannot open input device 
(EE) preInit failed for input device "configured mouse"
no core pointer

fatal server error: 
failed to initialize core devices

My Xorg.conf looks like this for my mouse and keyboard setup

section "input device"
identifier "generic keyboard"
driver "kdb"
option "corekeyboard"
option "Xkbrules" "Xorg"
option "XkbModel" "pc104"
option "XkbLayout" "us"
end section
section "inputdevice"
identifier "configured mouse"
driver "mouse"
option "Corepointer"
option "device" "dev/input/mice"
option "protocol" "ImPS/2"
option "Emulate3buttons" "true"
option "ZAxismapping" "4 5"

When I reconfigured my xorg file it did run me through mouse setup and i think i messed something up when doing so. I think generic drivers would probably get me out of this problem. if someone can help me out with this it would be great. 
I do have a Belkins wireless keyboard and mouse if that matters. 

Thanks for your help that you may be able to give me.

---

