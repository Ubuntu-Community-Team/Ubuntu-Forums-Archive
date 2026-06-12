---
title: "Screen Resolution"
date: 2005-07-18
forum: Desktop Environments
---

### Post by elfece on 2005-07-18
Hi, i have both windows and ubuntu installed on my PC, i jave a 17'' screen and my graphic card is a nVidia Riva TNT2, in windows, the maximum screen resolution is 1280X1024, but in ubuntu the maximum screen resolution is 1024X780, does anyone know how to use a higer resolution in ubuntu???
Thanks!!!

---

### Post by evilghost on 2005-07-18
[http://ubuntuforums.org/showthread.php?t=49260](http://ubuntuforums.org/showthread.php?t=49260)

---

### Post by frodon on 2005-07-19
If you're newbie type in a terminal : ```
sudo dpkg-reconfigure xserver-xorg
```
If not you have to edit your /etc/X11/xorg.conf file, most of resolution problem come from wrong refresh parameters ```
Section "Monitor"
	Identifier	"emachines"
	Option		"DPMS"
	**HorizSync**	30-70
	**VertRefresh**	50-160  
EndSection
```
Put in **HorizSync** and **VertRefresh** parameters the values corresponding to your screen specification.
If it still not works post here your xorg.conf file.

---

### Post by Sionide on 2005-07-19
Be careful when altering your HorizSync and VertRefresh values because entering the wrong ones can and will physically break your monitor. So make sure you get the right ones, they can be found in your monitors instruction manual. Google for it if you don't have a hard copy..

---

