---
title: "ATI drivers not installing because xorg.conf: &quot;Disable&quot; is not a valid keyword in thi"
date: 2009-04-15
forum: General Help
---

### Post by FaizanKazi on 2009-04-15
I was following this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

and just when i tried to do:
sudo aticonfig --initial -f 

i got the error: 
Parse error on line 34 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.

I had installed the restricted drivers using envyng before and they didnt work so well, so I had uninstalled them.

and so when this manual install of the new drivers didnt work, I thought that I should at least try to use envyng again, so i used it and it finished rather quickly and asked me to restart, and the drivers are working fine (as reported by fglrxinfo) but the ati catalyst control center wont work.

---

### Post by Tim Sharitt on 2009-04-15
Can you post your xorg.conf? 

Is there any particular reason you are installing them manually?

---

### Post by FaizanKazi on 2009-04-15
Oops... ok, so basically I got a little impatient and decided to enable the ati drivers from within Ubuntu's Hardware drivers GUI and it fixed everything... 
Now, the Xorg looks normal, drivers are giving me the same performance with glxgears that I was getting a couple minutes back after installing the ati drivers manually, AND catalyst control center now works!!

so I dont think ill be bothering with manually installing the latest ati drivers at all now, because I have nothing to gain.

here is my current Xorg after installing the ati drivers from Ubuntu's restricted drivers manager:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

previously, the Xorg looked like this:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection

```

thanks for you help! 

> **Tim Sharitt said:**
> Can you post your xorg.conf? 

Is there any particular reason you are installing them manually?

---

