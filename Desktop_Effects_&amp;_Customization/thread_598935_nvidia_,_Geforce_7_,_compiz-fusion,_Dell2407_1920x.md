---
title: "nvidia , Geforce 7 , compiz-fusion, Dell2407 1920x1200 resolution, screenshot problem"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by Sangmin Yu on 2007-10-31
I upgrade faisty fawn to gutsy gibbon 2 weeks ago.

My Spec
 : Nvidia Geforce 7 
 : Dell 2407 (1920x1200)

Problem is..
 * I can use 1920x1200. but, if I capture screen, I have below.
 * nvidia-setting is not running. that sw don't get geforce 7 infomation

I don't find solution this problem. So many time spent..

I try...
 * remove all package about compiz-fusion , reinstall
   * include gnome-compiz
 * using envy (special driver)
 * changing xorg.conf. 

xorg.conf 's about this subject part

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option      "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Option      "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 2407WFP (Digital)"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
 ...emit..
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

and I attach this full file


When I use feisty fawn, It ran well. 
Anybody have some other method?

---

### Post by Rowdy73 on 2007-11-29
Subscribing..

---

