---
title: "top part of the Monitor screen flickers"
date: 2010-03-30
forum: Desktop Environments
---

### Post by ruhollah on 2010-03-30
I have "flickering" problem with my LCD monitor in buntu 9.10. the top part of the monitor screen flickers horizontally and vertically (mainly horizontally). I did update manager, but it did not help. also I tried to manually edit the xorg.conf and add some vertical and horizontal frequencies, but no improvement (display did crash and I recovered the xorg.conf). 
do you have any suggestion? 
here are some specs:
my desktop is gnome 
monitor: Dell 2407WFP 24"
graphic driver: NVIDIA 
Driver Version:185.18.36

xorg.conf content:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

