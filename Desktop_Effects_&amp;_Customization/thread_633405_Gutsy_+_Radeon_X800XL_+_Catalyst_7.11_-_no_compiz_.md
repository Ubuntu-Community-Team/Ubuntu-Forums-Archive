---
title: "Gutsy + Radeon X800XL + Catalyst 7.11 - no compiz effects :("
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by niallporter on 2007-12-06
Hi all,

I have an old Dell Precision 340 (P4 32bit, 1GB) which I have Ubuntu 7.10 x86 installed on.  I recently upgraded gfx card in my other PC so installed the old Radeon X800XL AGP card into the Dell as I'd heard the ATI catalyst drivers now support AIGLX so will work with compiz.  I have the 7.11 drivers installed but can't enable desktop effects, I just get the message saying just that.  I tried adding some stuff to xorg.conf but it didn't help.  I've copied my xorg.conf file in below.  Can anyone help me get it working?  I have read reports that it should work now!

Cheers
Niall

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	"glx"
	Load	"dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Modes	"1920x1200"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option	"AIGLX"	"on"
EndSection

```

---

### Post by melojo on 2007-12-06
I have a x850 pro and  the only way I could get the new 7.11 drivers to work was to install xgl server but not enable desktop affects through ubuntu.  There is a new setting called GL Desktop after you install the 7.11 drivers and you can enable it there.  Your not supposed to need xgl server because of ati's aglx, but thats the only way I could get it to work and it ran slower than Ubuntu's restricted driver. Here is a thread about it.  [http://ubuntuforums.org/showthread.php?t=628718](http://ubuntuforums.org/showthread.php?t=628718).  You might try uninstalling 7.11 drivers and go with Ubuntu's restricted driver.

---

### Post by niallporter on 2007-12-06
Hmm ok but I have seen it working pretty well on an X300 without using XGL so I'd like to try and avoid that just now.  I had a look through that thread and it gave me an idea.  My fglrxinfo output tells me I'm using the Mesa OpenGL drivers, not ATI's ones.  I remember from trying this card on Feisty with older ATI drivers that that indicated a problem but just needed a change to xorg.conf to fix.  Can anyone tell me if I'm right?

---

### Post by melojo on 2007-12-06
Yea it sounds like your 7.11 Drivers didn't install.  post your xorg.conf so other users can take a look and maybe someone will be able to provide you with more help. 

xorg.conf can be foud in /etc/X11

---

### Post by macaholic on 2007-12-06
Follow [ this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3") guide if you think you installed them wrong. Installing from the .run file will not work.

---

### Post by niallporter on 2007-12-07
> **melojo said:**
> Yea it sounds like your 7.11 Drivers didn't install.  post your xorg.conf so other users can take a look and maybe someone will be able to provide you with more help. 

xorg.conf can be foud in /etc/X11

I already posted it, it's in my OP!

---

### Post by Ub1476 on 2007-12-07
Doesn't the built in graphic drivers support the x800 (and below)?

---

### Post by melojo on 2007-12-07
> **niallporter said:**
> I already posted it, it's in my OP!

For some reason I didn't see it.  I reinstalled 7.10 and tried the new drivers again and followed this link exactly [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).  I did get it to work but it runs slower than the Ubuntu's restricted drivers.

---

