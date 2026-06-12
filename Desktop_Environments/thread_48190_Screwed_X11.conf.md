---
title: "Screwed X11.conf"
date: 2005-07-11
forum: Desktop Environments
---

### Post by N'Jal on 2005-07-11
Ok i have gotten a new monitor, and i read once that it's best to reconfigure xorg to deal with the new monitor, so i plug it in, type in the failsafe terminal sudo dpkg-reconfigue xserver-xorg go through the 'wizard' watching carefully for screen res question's as i had problem's upgrading from warty to hoary and the resolution was at 800X600 now, i answer these question's as they need be, hoping to get 1024X768, but NOOOO im stuck on 600X400 i've run sudo dpkg-reconfigue xserver-xorg many times now, i even manually looked at my x11.conf file and everything say's 1024X768... So im stumped.

Any ideas?

---

### Post by ImaMadGoat on 2005-07-11
do a quick seach of the forum for 'resolution' there's about 7 different ones that have the info you need

chad

---

### Post by N'Jal on 2005-07-11
Nah tryed lot's of them compairing their xorg.conf file's to mine, but i can't see any errors.

Here's my file, if it helps

---

### Post by ImaMadGoat on 2005-07-11
you need the monitor specs to fix your file. If you chose simple mode when reconfiguring the xserver, it wouldn't ask you what your horisynch and vertrefresh rates are,

these are mine and I am using a start 17in CRT monitor, you need to add these two lines to the monitor section of your file. 

so what right now looks like this:

Section "Monitor"
	Identifier	"ADI CORP"
	Option		"DPMS"
EndSection

needs to look like this

Section "Monitor"
	Identifier	"ADI CORP"
	Option		"DPMS"
	HorizSync 30-70
	VertRefresh 50-140
EndSection

that should fix your problem. btw, this was covered in about 7 other posts if you search the forum for resolution. Ya just gotta seach a bit deeper.  :)

---

### Post by az on 2005-07-11
Perhaps you need to kill X before you auto configure your hardware.

CRTL-ALT-F1
log in
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

---

### Post by N'Jal on 2005-07-11
> Section "Monitor"
Identifier "ADI CORP"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-140
EndSection

This fixed it, though i had gone through all stages of the reconfiguration of the xserver but it just didn't add the values, strange...

Sorry but i just couldn't find the posts you were talking about, if there are several please feel free to remove this thread then.

Thanks again.

---

