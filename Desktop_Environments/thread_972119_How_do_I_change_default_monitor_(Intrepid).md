---
title: "How do I change default monitor (Intrepid)"
date: 2008-11-05
forum: Desktop Environments
---

### Post by yusuo85 on 2008-11-05
Im having a bit of trouble changing my default monitor, I've tried auto-detecting monitors through screen resolution inside system>preferences, but when i rebooted all I got was a flashing screen on my primary monitor.
My hardware is laptop 15" lcd with and external 17" crt running via vga with an 128MB ATi Radeon R200 Express.
 If anyone can help it really would be appreciated its hard to watch movies through an lcd monitor.

All of my xorg.conf file is below

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

