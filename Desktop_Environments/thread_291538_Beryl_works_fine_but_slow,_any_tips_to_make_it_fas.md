---
title: "Beryl works fine but slow, any tips to make it fast?"
date: 2006-11-02
forum: Desktop Environments
---

### Post by Isoss on 2006-11-02
Hello.

I have successfully installed beryl on an intel laptop with ati vga, 1700MHz Centrino, 768MB RAMs, but it slows down my system! I followed the steps [here](http://doc.gwos.org/index.php/BerylOnEdgy), I updated my repos, then edited my xorg.conf, it looks like this now:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver "radeon"
	BusID		"PCI:1:0:0"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	#Option "AGPMode" "2"
	Option "AGPFastWrite" "on"
	Option          "TripleBuffer" "true"
EndSection

```
then ran ```
 sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```
then rebooted and beryl worked but slowed my system down! 

I am not sure what these configurations which I added to my xorg.conf do ... anyone can explain each option? and what can I do in order to make things faster? cuz I suppose I have a good laptop!

I'll appreciate any help

---

### Post by boban on 2006-11-02
I think this is because you use open source radeon drivers... If your VGA is supported by closed source drivers try running Xgl/Beryl with them...

See:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) - installation of ati drivers

[http://ubuntuforums.org/showthread.php?t=285905](http://ubuntuforums.org/showthread.php?t=285905) - link and some problems with installation of xgl/berly

Btw. are you using Dapper or Edgy?

---

### Post by Isoss on 2006-11-10
edgy, in fact I am not that much into drivers and hardwares. how would I know that my VGA is supported by closed source drivers?

Thanks

---

### Post by boban on 2006-11-10
> **Isoss said:**
> edgy, in fact I am not that much into drivers and hardwares. how would I know that my VGA is supported by closed source drivers?

Thanks

Check here: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

---

