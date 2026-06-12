---
title: "VGA monitor not working"
date: 2008-12-11
forum: General Help
---

### Post by k4rizma on 2008-12-11
Hello all, 

First post here and in need of some help. When I plug my monitor into the VGA port on my laptop for some reason it will not display anything at all. I have a report to give in class (on ubuntu!) and this is the only thing standing in my way. I have a HP Pavillion dv6000 running Ubuntu Intrepid Ibex 8.10 with the latest nV

I've looked around (for about 2 days) and it seems I need to change some settings in my xorg.conf file in /ect/x11/  

Here is what my xorg.conf file looks like

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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

I'm very very new to Linux but learning. It could be another issue all together but I wouldn't know at this point. 

Thanks in advance :)

---

### Post by ettercap on 2008-12-11
if u have an nvidia card then i suggest u use the restricted driver instead of the .run file the .deb file is much easier to install

the driver accessible through synaptic

---

### Post by eBoxNet on 2008-12-11
did you try to plug your monitor before you boot up your computer?try it before you edit any files.

---

