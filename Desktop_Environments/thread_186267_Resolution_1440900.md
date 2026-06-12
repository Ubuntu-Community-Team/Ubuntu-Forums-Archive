---
title: "Resolution 1440*900"
date: 2006-06-01
forum: Desktop Environments
---

### Post by thirdmusketeer on 2006-06-01
Hi

I don't know why I am not seeing the option 1440 x 900 under 
Preferences > Screen Resolution in Gnome


my /etc/X11/xorg.conf is as follows

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"laptop"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"VMWare Inc [VMWare SVGA II] PCI Display Adapter"
	Driver		"vmware"
	BusID		"PCI:0:15:0"
	VideoRam	65536
EndSection

Section "Monitor"
	Identifier	"Dell 700m monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
	Modeline	"1440x900@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VMWare Inc [VMWare SVGA II] PCI Display Adapter"
	Monitor		"Dell 700m monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by onesojourner on 2006-06-01
I had the same problem running the live cd on a dell inspiron E1405. had to run it in safe graphics mode.

---

### Post by macheadPDX on 2006-06-01
I'm also experiencing this in my iMac G4 using the Live CD... Now I'm hesitant to upgrade to Dapper. :-(

---

### Post by thirdmusketeer on 2006-06-01
In my Gnome, under System>Preferences>System Resolution,
 
the resolutions being shown are not matching with my xorg.conf, where does that read its values from, maybe I need to change things there, I am sure it is capable of showing me 1440 x 900 resolution, 


Thanks

---

### Post by Horizon on 2006-06-02
[QUOTE=thirdmusketeer]
	Modeline	"1440x900@60" 83.91 1280 1312 1624 1656 800 816 824 841[/QUOTE]
Shouldn't that @ sign be an underscore ? like "1440x900_60" ...Well that's how i used to do it before dapper started recognising my display modes properly :-k

---

### Post by TrAvELAr on 2006-06-02
The 700m only does 1280x800.  Even then, you'll need to install 855resolution and use it before you can select 1280x800.  

Hope that helps.

---

### Post by thirdmusketeer on 2006-06-02
I am running it on 700m but I have connected externally to Xerox XR6-19DW which has a max resolution of 1440 x 900. I am easily able to run things on 1280x800. I selected several options while I was installing ubuntu and now only those options show, none other.

---

### Post by dmorel on 2006-06-02
I went through a very hard time to get 1920x1200 as an option for my monitor. The searching I did led me to this solution... (I'm presuming your using a depth of 24, if not change below as needed...)
in xorg.conf edit (sudo gedit /etc/X11/xorg.conf) the section that currently looks like this:
```

SubSection "Display"
Depth 24
Modes "1440x900" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
EndSubSection

```

to have ONLY 1440x900, like this:
```

SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection

```

restart X, ctrl+alt+backspace.

If that doesn't work.... 
One other thing that was suggested to me by forum member redXninja for this kind of issue (but did not work for me) is below. Remember this advice was for 1920x1200, so change to your 1440x900 where appropriate:
> 
This is how I do my widescreen setting in xorg.

Open up the terminal and type this comand.


gtf 1900 1200 60

what that mean is 1900x1200 at 60Hz.
gtf will out put some thing like this...

# 1904x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 191.96 MHz
Modeline "1904x1200_60.00" 191.96 1904 2032 2240 2576 1200 1201 1204 1242 -HSync +Vsync

Copy that to the Monitor section in your xorg.conf...It looks like this.

Section "Monitor"
Identifier "FPD2185W"
VendorName "GateWay"
ModelName "FPD2185W Widescreen"
Option "DPMS"
HorizSync 31.0 - 81.0 # use your own lcd settings for this
VertRefresh 56.0 - 76.0 # use your own lcd settings for this

# 1904x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 191.96 MHz
Modeline "1904x1200_60.00" 191.96 1904 2032 2240 2576 1200 1201 1204 1242 -HSync +Vsync

EndSection


Hope this helps a bit...

---

### Post by Simian on 2006-06-02
I had this problem when I had quick go with FC5. I ended up fixing it by changing the vertical sync values. I copied them from another user with 1440x900. I have a dell inspiron 9300 with 1440x900. I'm not at home at the moment but if you wont I can copy my xorg.conf for you?

---

### Post by souki on 2006-06-02
I don't have any problem with my laptop's 1440x900 display

maybe your modeline is wrong, I don't have any definition in my xorg.conf

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection
``` 
also, gnome resolutions are different from what I have in xorg.conf, but, for me, gnome shows more resolutions

in my "Screen" section:
```

        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
``` 
and from gnome, I have:
"1440x900" "1024x768" "800x600" "640x480"
+ "1280x768", "1152x864", "1024x600"

---

### Post by thirdmusketeer on 2006-06-02
It turns out that the problem is somehow due to VMware. I reinstalled and i still couldn't get the required resolution. I will now be bugging the VMware guys.

Thanks

---

