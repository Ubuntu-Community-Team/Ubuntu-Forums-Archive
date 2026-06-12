---
title: "Weird Graphics Display"
date: 2006-07-20
forum: Desktop Environments
---

### Post by mosestruong on 2006-07-20
I'm having problem with the graphics display - i sometimes get a "corrupt display" when using Dapper. I've attached a screenshot of what I mean.

The computer I'm using is a Compaq Presario 2800. 

my xorg.conf includes:

```

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel"		"true"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"true"
	Option		"EnablePageFlip"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

```

Are there any remedies? This problem started after upgrading to Dapper. Thanks.

---

### Post by philippe_carlo on 2006-07-20
Install the fglrx driver for your ATI card. Here's the howto: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

### Post by mosestruong on 2006-07-20
lspci gives me:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

and i believe fglrx only supports 8500 and later...

---

