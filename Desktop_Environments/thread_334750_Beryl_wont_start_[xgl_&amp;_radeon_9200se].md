---
title: "Beryl wont start [xgl &amp; radeon 9200se]"
date: 2007-01-09
forum: Desktop Environments
---

### Post by ffxr on 2007-01-09
hi..

i have searched ubuntu & beryl forums, the web & asked on ubuntu IRC channels, to find a resolution for this problem.. its seems to be relatively common but i have yet to find a definitive and clear answer. ve tried many different things but i just cant get it to work..

pls help if you can.. 

my problem is beryl wont start.. it gives the following error

[B]sudo beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl-xgl: No composite extension[/B]

sudo beryl-manager gives an identical error..

i am 99% sure fglrx driver & xgl are working fine.

[B]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)[/B]


[B]ps axw | grep -i xgl
 5318 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/local/bin/startxgl.sh
 5321 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/local/bin/startxgl.sh
 5323 ?        SL     0:01 Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer
 6115 pts/2    S+     0:00 grep -i xgl[/B]

i have attached my xorg.conf, for anyone who is willing to assist..
i can also paste up my  Xorg.0.log if that will help ( i can see no discernible errors )
(pls let me know if you need any more info from me )


also..can someone pls outline the differences between xgl & AIGLX..? i have spent the best part of 2 days configuring my card & xgl.. and am very unwilling to scrap all that graft now...



thanks for your time..

---

### Post by Waappu on 2007-01-09
Hi

Did you create XGL session and login to it?

---

### Post by ffxr on 2007-01-09
yup

---

### Post by Waappu on 2007-01-09
Hi

I have ATI 9250 card and didn't get XGL to work. AiGLX working me perfect. I don't know exact what is difference on XGL and AiGLX. If you can use open source driver and want to try AiGLX here is guide that I folowed.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Waappu on 2007-01-09
Hi

I think you should remove this from /etc/X11/xorg.conf. 
```
Option      "Composite" "On"
```
Composite isn't supported on fglrx driver

---

### Post by ffxr on 2007-01-09
ok i took it out.. i only had added it recently anyway... so theres no change in results...

it begs the question, does beryl need Composite support to work?

---

### Post by ffxr on 2007-01-09
[B]
lsmod | grep fglrx
fglrx                 406988  21
agpgart                34888  2 fglrx,nvidia_agp[/B]

why does this command show this output for my ATI card?
would this be related to my issue?

---

### Post by ffxr on 2007-01-09
[B]dmesg |grep -i agp
[17179570.256000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179589.596000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.616000] agpgart: Detected NVIDIA nForce2 chipset
[17179589.620000] agpgart: AGP aperture is 64M @ 0xe0000000
[17181047.656000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17181047.656000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17181047.656000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17181047.656000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17181047.656000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)[/B]

it seems an nvidia card is being detected.. (iknow my agp card is ati, but i believe their is an nvidia chipset on my motherboard) im too new at this to this melarkey to know if this the cause of my problems...

---

### Post by Waappu on 2007-01-09
Hi

> **ffxr said:**
> 
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl-xgl: No composite extension
I'm not expert but I think problem is in XGL. You can try AiGLX and open source drivers.

---

### Post by ffxr on 2007-01-10
i would prefer to use xgl+beryl with my ATI card as i have read it runs a lot faster than AIGLX... [+ i spent 2 days getting xgl running *properly* ]

can ANYONE offer any other pointers as to how i might be going wrong.. ?

---

### Post by Waappu on 2007-01-10
Hi

Yes, XGL should be faster. It seems that I can't help.
If you haven't see this yet look how others had get ATI card workig
[http://ubuntuforums.org/showthread.php?t=221320](http://ubuntuforums.org/showthread.php?t=221320)

---

### Post by misha680 on 2007-01-13
Only thing i can't understand is why you are running beryl with sudo, you shouldn't have to preface it with sudo, don't know if this will fix it. Also, try adding beryl-manager to your GNOME session (System -> Preferences -> Sessions), it doesn't make any sense but I remember having some kind of slightly similar problem adn thsi worked for me.

Misha

---

### Post by sheep333 on 2007-01-13
I need help. Beryl wont start this is my xorg:



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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection

---

### Post by Waappu on 2007-01-14
Hi

Have you installed XGL, created XGL session and login to that session?

---

### Post by sheep333 on 2007-01-14
yeah I did. I followed the wiki.beryl-project tutorial

---

### Post by Hendrixski on 2007-01-14
Hey, I just got Beryl working for the first time today.  Turns out that I just needed the most recent ATI driver from ATI's website.  I had installed ATI drivers from Ubuntu 3 or 4 months ago.

It finally works, it looks sweet!

---

### Post by ffxr on 2007-01-29
I ended taking earlier advise.. (thanks guys :) ) & used the AIGLX drivers. Beryl worked out of the box with the default install of xubuntu. m still not entirely happily with 3d performance in other areas' but beryl does work perfectly. :guitar: 

Hendrixski, can you post your xorg.conf just to satisfy my curiosity.


(thanks for everyones input)

---

### Post by koshari on 2007-01-29
the way i see it you have 2 choises, aiglx or scrap the 9200 card, 

i dont know of any cases where the 9200/9250 card has run beryl using xgl.

and aiglx will be slow on this card but at least it will work.

i threw my 9250 in another box and replaced it with a 6200le nvidia and it works a treat.

---

### Post by koshari on 2007-01-29
> Turns out that I just needed the most recent ATI driver from ATI's website

laters fglrx drivers dont work with older ati cards,

---

