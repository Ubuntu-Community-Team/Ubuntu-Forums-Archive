---
title: "terminal and windows bar failure"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by blackriven on 2008-03-11
I installed the 3d windows plugin by following the directions in this [post]("http://forum.compiz-fusion.org/showthread.php?t=5303"), and the that bar on windows that has the close and minimize buttons disappeared. I went to the options and nothing helpful came out of that, but I noticed that enabling and disabling 3d windows or the cube returned the bar, except that the cube no longer worked even if supposedly enabled. I have nautilus desktop disabled to allow multiple wallpapers and when the cube failure happened they all collapsed to that one wallpaper I defined through normal means, which leads me to believe that Ubuntu maybe reverted back to default because of some error relating to the 3d windows plugin and that's how I got the missing bars back. 
Anyway, I uninstalled the plugin and restarted, but not only did it not solve the problem, now the terminal doesn't work. When I try to run it I only get a white Window. Interestingly enough, the general infrastructure seems to be working (if I click on where the menu options should be I get the menus), and I can copy paste from it, but other than that everything's white. Other applications seem to be working normally. 
Help, anyone...?

I have Ubuntu 7.10

---

### Post by decard_pain on 2008-03-11
i've had a problem like this too .to fix it i had to add this line to the xorg.conf
Option      	"AddARGBGLXVisuals"      "True"
then restart and it should be fixed

---

### Post by blackriven on 2008-03-11
OK, where in the file do I add the line?

---

### Post by decard_pain on 2008-03-11
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option      	"AddARGBGLXVisuals"      "True"

thats the section your looking for.it worked for me

---

### Post by blackriven on 2008-03-11
OK that did it, thanks.

---

