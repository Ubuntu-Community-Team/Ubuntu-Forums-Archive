---
title: "How-to Ubuntu Edgy + AIGLX + Beryl on Intel GMA 950 with multi-head"
date: 2007-01-17
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2007-01-17
Hi,

I have a laptop with a [Mobile Intel GMA 950]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_950") graphics processor integrated on a [Mobile Intel 945GMS]("http://en.wikipedia.org/wiki/List_of_Intel_chipsets#Intel_Core_Chipsets") chipset. It should be able to allocate up to 224 MB of video memory, borrowed from system memory. I have 1.5 GB of DDR2 system memory. The CPU is an [Intel Core Solo U1400]("http://en.wikipedia.org/wiki/List_of_Intel_Core_microprocessors#.22Yonah.22_.28ultra-low-voltage.2C_65_nm.29") 1.2 Ghz.

*Edit: Intel [says]("http://www.intel.com/products/chipsets/gma950/index.htm") the GMA 950 can handle up to 224 MB but my laptop's manufacturer UK page [says]("http://www.vaio.sony-europe.com/view/View.action?section=Products_ITE&productcategory=%2FComputing%2FVAIO+Notebooks%2FVN+TX+Series&productmodel=%2FComputing%2FVAIO+Notebooks%2FVN+TX+Series%2FVGN-TX3XP%2FB&productsku=VGNTX3XP%2FB.CEK&site=ite_en_GB&page=ProductTechnicalFeatures") 128 MB, and US page [says]("http://vaio-online.sony.com/prod_info/vgn-tx47gp_b/specifications.html") it too. How can I know?*

The GPU runs at 250 MHz and have VLC, iDCT, hardware motion-compensation, and dual video overlay windows (1 HD + 1 SD). Vertex Shader version 3.0. Pixel Shader 2.0. No  Hardware T&L!

I use a dual-head setup. The two displays do not use the same resolution. I have one screen at 1366x768 and one at [SIZE=-1]1680x1050, which make 2.8 [/SIZE]megapixels to manage.

I'd like to use Beryl with AIGLX on this dual-head Ubuntu Edgy. So my first question is, will this run at all? If yes, will it run smoothly?

And my second question is, is there a how-to somewhere, to build exactly that setup?

Thanks!

---

### Post by Jonathan Métillon on 2007-01-21
I followed the [how-to at Beryl Wiki]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX") and got it working with one screen only. And it does very smoothly!

Here is the xorg.conf I use for it, relevant sections only:

```
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
  Load  "dri"
  Load  "dbe"
  Load  "glx"
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
  Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1366x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection
```Now I try to use it with dual screen. And it crashes! I get into the same issue as described in [this thread]("http://ubuntuforums.org/showthread.php?p=1793987#post1793987").

So my question is now: **why is my laptop crashing when trying to use XGL an dual screen at the same time?**

Here is my xorg.conf for the dual screen setup, relevant parts only:

```
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
  Load  "dri"
  Load  "dbe"
  Load  "glx"
EndSection

Section "Device"
    Identifier    "GMA950"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    VideoRam    262144
  Option          "CacheLines" "8192"
    Screen        0
  Option      "MonitorLayout" "CRT,LFP"
  Option  "XAANoOffscreenPixmaps"
EndSection

Section "Device"
    Identifier    "GMA950-VGAOUT"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    VideoRam    262144
  Option          "CacheLines" "8192"
    Screen        1
  Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Internal"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "2007FPW"
    Option        "DPMS"
    HorizSync       30-81
  VertRefresh     56-76
EndSection

Section "Screen"
    Identifier    "Screen-1"
    Device        "GMA950"
    Monitor        "Internal"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1366x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen-2"
    Device        "GMA950-VGAOUT"
    Monitor        "2007FPW"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1680x1050"
    EndSubSection
EndSection

Section "ServerFlags"
    DefaultServerLayout    "Multihead"
EndSection

Section "ServerLayout"
    Identifier    "Multihead"
    Option        "Xinerama" "false"
    Screen 0     "Screen-1" 0 0
    Screen 1     "Screen-2" Above "Screen-1"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
    Identifier    "Default"
    Screen        "Screen-1"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection
        
Section "Extensions"
  Option "Composite" "Enable"
EndSection
```Thanks!

---

### Post by robert114 on 2007-01-25
I'll get a simular configuration and will give it a try
But i'm not a Linux scientist so maybe and just maybe I'll be able to help you

---

### Post by Jonathan Métillon on 2007-01-25
> **robert114 said:**
> I'll get a simular configuration and will give it a try
But i'm not a Linux scientist so maybe and just maybe I'll be able to help you

Sounds good Robert! At least I'm no more in a monologue.

---

### Post by Laterix on 2007-01-26
I have very much same specs. Is your Laptop Sony TX series? I have only 512ram and wobbly windows is little slow. Other wise Beryl runs pretty well. Maybe I should buy more ram...

---

### Post by Jonathan Métillon on 2007-01-26
> **Laterix said:**
> I have very much same specs. Is your Laptop Sony TX series? I have only 512ram and wobbly windows is little slow. Other wise Beryl runs pretty well. Maybe I should buy more ram...

Yep, a TX3 as named in Europe. I think in USA it's a TX800 or TXN17. And TX93 in Japan.

Wobbly windows have been fluid here. In fact, I could feel slow down in Beryl only by activating motion blur effects.

---

### Post by robert114 on 2007-01-26
damn I'm still waiting for my lap...

---

### Post by discord on 2007-02-13
I have the same issues and would really like to get dual monitors working. I cannot get a second head stable by itself either. I can toggle between displays with the keys on the board but would like a stable monitor with the video out port, with or without the laptops display. Even without beryl I would like stable external monitor port

---

### Post by Jonathan Métillon on 2007-02-13
Discord,

I think you should start another thread for this issue. My external monitor port has no stableness problem, and this is not related to Beryl working on dual screen setup over a GMA 950.

Good luck stabilizing your output! 

(Btw, did you contact your support, are you sure it's not hardware failure?)

---

### Post by robert114 on 2007-02-13
Damn, allmost forgot about this forum... but I havn't done any research yet because of the lac of free time....

I have to say everything works just fine on my laptop but havn't tried the multi head

---

### Post by Josh8178 on 2007-03-09
Help! I can't seem to get AIGLX working, I followed the guide on how to enable it, I am running Kubuntu 6.10. I tried the Mandriva One 2007 and it worked out of the box so my hardware can run it. I Really love Kubuntu and this would be the icing on the Cake, here is my xorg.conf file.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
 Load	"dri"
 Load	"dbe"
 Load	"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
  Option  	"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

---

### Post by Jonathan Métillon on 2007-04-03
Hi Josh8178,

I don't think your issue is related to this very specific thread I started. Please post your issue in a more related thread or start a new one.

Thank you!

---

### Post by Chrisj303 on 2007-04-03
Check out towards the end of this guide : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)


chrisj303

---

### Post by Jonathan Métillon on 2007-04-03
Thanks Chrisj303,

Well it says:

> You'll have to disable either dual head mode or the 3D desktop while using the other.> 3D desktops (*Beryl*) should be disabled when using a dual-head setup, otherwise the X server might crash! Not good :-)

But is says too:

> Extended desktop and video mirroring do **NOT** work with *Beryl* just yet!Does the *yet* means that people are working on making Beryl (or Desktop Effects in terms of Ubuntu Feisty) works with GMA 950 and dual-head?

Can you point me to where I should be watching for the evolution of this issue?

Thanks!

---

### Post by Chrisj303 on 2007-04-04
> **Jonathan Métillon said:**
> Thanks Chrisj303,

Well it says:

Not good :-)

But is says too:

Does the *yet* means that people are working on making Beryl (or Desktop Effects in terms of Ubuntu Feisty) works with GMA 950 and dual-head?

Can you point me to where I should be watching for the evolution of this issue?

Thanks!

Yeah, i would go here : [www.beryl-project.org/](www.beryl-project.org/) - 8k

That should sort you out,!

chrisj303

---

### Post by Jonathan Métillon on 2007-04-06
I got updates about this issue!

I moved the thread to Beryl.org:
[http://forum.beryl-project.org/viewtopic.php?f=36&t=5646](http://forum.beryl-project.org/viewtopic.php?f=36&t=5646)

---

### Post by mspolar on 2007-04-24
thanks ~ intel 950 works great...

---

### Post by Grey on 2007-07-24
I'm having a very very similar problem with similar hardware.  The difference over here is that I am NOT using dual head, and my xorg.conf is pretty much identical to the one you posted that you said worked.  I was developing a 3D application last night, and it was plain miserable, as about every 10th time I ran it, it would lock up my X server, and restart.  I really don't have anything to add to this issue.  I have been fighting with this problem on various levels for months, and I have yet to find a solution.  I'm actually considering upgrading to Gutsy, in the hopes of finding new, working drivers.

---

