---
title: "compiz-fusion frame-rate problem"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by nikolaos on 2008-01-16
Hi all, i was perfectly using beryl in my feisty distro. i upgraded to gutsy 2 days ago and followed this guide [http://ubuntuforums.org/showthread.p...org.conf+gutsy](http://ubuntuforums.org/showthread.p...org.conf+gutsy)
trying to set up compiz-fusion in my macbook.
I know that the Graphic card in my MacBook is not an ATI but i couldn't find a guide for mac users anywhere,
The thing is that when i
Code:

```
sudo apt-get install xserver-xgl
```

compiz starts but my frame rate is awful, i think it has something to do with my xorg.conf file so i am posting the relevant sections.

```


Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option   "XAANo0ffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4

```
i hope you can help me.

---

### Post by CC_machine on 2008-01-16
MacBooks have only a weak integrated intel chipset for graphics so, sorry, your laptop simply isn't powerful enough to run compiz-fusion well.

I find beryl to be slightly faster but not worth the effort, instead i use this "trick":
change to 16-bit colour mode. While the difference is somewhat visible and can be annoying (especially if you need the rich colour depth for graphic applications like the GIMP), I like the benefit of faster graphics in compiz and games, etc.

in your xorg.conf, do the following:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
```

leave everything else as is, only change the 24 next to DefaultDepth to 16. save, restart X, and see what happens. To change it back, simply open xorg.conf again, and change it back to 24.

---

### Post by nikolaos on 2008-01-19
thank you very much CC_machine. The problem is now that when i try to enable 
-Normal
-Extra or 
-Custom effects i get a 
"Desktop effects could not be enabled"  message. 
any ideas?

---

