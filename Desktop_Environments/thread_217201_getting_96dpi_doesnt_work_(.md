---
title: "getting 96dpi doesnt work :("
date: 2006-07-16
forum: Desktop Environments
---

### Post by quick on 2006-07-16
hi i tried to improve my fonts 
and tried to get real 96dp

i always get

xdpyinfo | grep resolution
  resolution:    87x96 dots per inch


xorg ignores my DisplaySize setting in xorg.conf 

Section "Monitor"
	Identifier	"HM903DB/DTB"
	Option		"DPMS"
	HorizSync 	30-132
	VertRefresh 	50-200
	DisplaySize	420 315
EndSection

according to the guide i should get 96x96 output from the command above but nothing works! :(

anyone knows why xorg is ignoring my config?

thanks in advance

---

### Post by Dubbayoo on 2006-07-16
Try System/Preferences/Font/Details/Resolution

Change the number and the size changes in real time.
You might also take a look at this site

[http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html](http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html)

---

### Post by Case_f on 2006-07-16
Setting DPI using DisplaySize should give you the optimal DPI for your monitor, which, depending on the actual size of your screen (given in DisplaySize) AND resolution you use, may or may not be 96dpi. So, 87x96 may very well be the optimal DPI for you. Are you sure X ignores your DisplaySize setting? Did you try to change the values to see if DPI changes as well? It should, as long as the resolution stays the same.

---

### Post by quick on 2006-07-17
@Dubbayoo
changing the dpi setting in gnome is still something else than the x.org config - thats just what i read :)

@case_f
yes X ignores my displaysize setting, i tried several values but end up with the same results all the time :)
maybe you are right and its the best already but shouldnt it be changeable? :)

greetings!

---

### Post by Case_f on 2006-07-17
Well, if you tried different DisplaySize values and nothing changes, then something is wrong, that's for sure. But as to what...:/

---

### Post by quick on 2006-07-19
the problem was the nvidia driver with its 

#Option "UseEdidDpi" "FALSE"

option if i uncomment this line it works :)
but it doesnt change my font noticeably so i just let it be as it is :) :-|

---

