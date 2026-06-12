---
title: "change resolution of logon manager"
date: 2006-01-17
forum: General Help
---

### Post by Choad on 2006-01-17
i prefer to work in 1024x768 resolution on my small monitor, and have changed the resolution in my profile, but the logon manager is still at 1200 x 1000.

what do i have to do to change that setting?

cheers

---

### Post by chadwick359 on 2006-01-17
I beleive that actually having kdm use a different resolution requires changing your xorg.conf. Changing the Modes in the  Screen section will manually set the resolution for X, and will force Kdm into that resolution.

(Code edited out because of a better description below, thanks Omnios.)

---

### Post by Omnios on 2006-01-17
I had a similar where log in would be at 17xx xxxx but got around that by opening xorg.conf.

 ```
sudo gedit /etc/X11/xorg.conf
```

 And taking out the 1792x1344.
 
 ```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"A91f+"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

 This will now use the next higher res for the bot up. Note you will not longer have that higher res in you set resolution in gnome.

---

### Post by Chris Tucker on 2006-01-17
theres a much cleaner way, not positive that this works, but it should still allow the system to use the 1200x1000 res. but just not sure if it will actually lower the kdm/gdm login res. sudo dpkg-reconfigure xserver-xorg  and go through everything, when it comes to monitor stuff go "medium" when you see that option.... then when it asks what your monitors *BEST* resolution is, choose what you want... note this is NOT the screen where you put a * or # next to the res's you want the computer to be allowed to use. this is after that.

---

### Post by Choad on 2006-01-17
[QUOTE=Chris Tucker]theres a much cleaner way, not positive that this works, but it should still allow the system to use the 1200x1000 res. but just not sure if it will actually lower the kdm/gdm login res. sudo dpkg-reconfigure xserver-xorg  and go through everything, when it comes to monitor stuff go "medium" when you see that option.... then when it asks what your monitors *BEST* resolution is, choose what you want... note this is NOT the screen where you put a * or # next to the res's you want the computer to be allowed to use. this is after that.[/QUOTE]
cheers, i did that and i hope it worked :)

---

### Post by karaluh on 2006-11-24
> **Chris Tucker said:**
> sudo dpkg-reconfigure xserver-xorg  and go through everything, when it comes to monitor stuff go "medium" when you see that option.... then when it asks what your monitors *BEST* resolution is, choose what you want...

Works for me, thanks.

---

