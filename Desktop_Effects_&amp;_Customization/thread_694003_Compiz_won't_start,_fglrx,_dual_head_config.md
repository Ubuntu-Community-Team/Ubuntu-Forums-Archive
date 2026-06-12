---
title: "Compiz won't start, fglrx, dual head config"
date: 2008-02-11
forum: Desktop Effects &amp; Customization
---

### Post by pormogo on 2008-02-11
Well a few week ago I decided to move away from the Mesa open source driver trying to fix and issue I identified in the following thread. 

[http://ubuntuforums.org/showthread.php?p=4276315#post4276315](http://ubuntuforums.org/showthread.php?p=4276315#post4276315)

I went ahead and installed the newest version of fglrx as outlined in the ubuntu wiki from ATI's website. I used the following command to generate my packages. 
*./ ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy*

I installed the 2 packages it generated *fglrx-kernel-source_8.452.1-1_amd64.deb* and *xorg-driver-fglrx_8.452.1-1_amd64.deb*. 2 other packages named *xorg-driver-fglrx-dev_8.452.1-1_amd64.deb* and *fglrx-amdcccle_8.452.1-1_amd64.deb* where also generated, I haven't run across the *fglrx-amdcccle_8.452.1-1_amd64.deb* package before so I decided not to touch it. I then used the aticonfig tool to setup my xorg.conf file with 
*aticonfig --initial*

After a restart everything appeared to be working great and continued to work well for the next few weeks. Then I got a DVI to VGA adapter and hooked up my second monitor. Everything was working as normal with the second monitor acting as a clone of my first display. But that's not what I wanted. So I decided to use the aticonfig tool to make this work (since I don't really know how to do dual monitors editing xorg.conf by hand). I don't remember the exact command I used but it looked something like this. 
*aticonfig --initial=dual-head --desktop-setup=horizontal --screen layout=right*

I copied the old config to .old and then ran the command. It generated a new Xorg.conf file for me and loaded up gmd after restarting X just fine. Upon entering Gnome though ubuntus default desktop effects manager did not load compiz. When I tried manually loading compiz I was greeted with the following error. 

[i]darthbator@superb-odifference:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e4a (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960
1024x768) to maximum 3D texture size (2048
2048): /usr/bin/compiz: line 229: [: too many arguments
/usr/bin/compiz: line 229: [: too many arguments
Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 1
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0[/i]

I checked to make sure rendering was working 

[i]darthbator@superb-odifference:~$ glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: RADEON 9800 XT
direct rendering: Yes
OpenGL renderer string: 
[/i]

glxgears zips by on both monitors. I'm not quite sure what the problem here is. Is dual monitor config broken with compiz for fglrx right now (wow that's specific)? Is there something wrong with my xorg.conf file???? I pasted the contents of my current xorg.conf file, as well as the output of the fglrxinfo command as well as dmesg|grep fglrx from my most recent reboot.

[i]darthbator@superb-odifference:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.1.7276 Release

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: 
OpenGL version string: 2.1.7276 Release
[/i]

Here is dmesg|grep fglrx

[i]~# dmesg |grep fglrx
[   45.210896] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, 
Starnberg, GERMANY' taints kernel.
[   45.233787] [fglrx] Maximum main memory to use for locked dma buffers: 1403 M
Bytes.
[   45.233824] [fglrx] ASYNCIO init succeed!
[   45.234226] [fglrx] PAT is enabled successfully!
[   45.234259] [fglrx] module loaded - fglrx 8.45.4 [Jan 16 2008] on minor 0
[   65.678406] [fglrx] Internal AGP support requested, but kernel AGP support ac
tive.
[   65.678698] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   65.678854] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of c
hipset)
[   65.679705] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   65.692956] [fglrx] GART Table is not in FRAME_BUFFER range 
[   65.693205] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   65.920407] [fglrx] interrupt source 20008000 successfully enabled
[   65.920669] [fglrx] enable ID = 0x00000004
[   65.920813] [fglrx] Receive enable interrupt message with irqEnableMask: 2000
8000
[   65.921070] [fglrx] interrupt source 10000000 successfully enabled
[   65.921216] [fglrx] enable ID = 0x00000005
[   65.921341] [fglrx] Receive enable interrupt message with irqEnableMask: 1000
0000
[   76.065596] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000005 not found i
n mutex list
[   76.124072] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000006 not found i
n mutex list
[   76.831174] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x0000000b not found i
n mutex list
[   76.874621] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x0000000c not found i
n mutex list
[/i]

And finally here is my xorg.conf file

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "Off"
        Option "XAANoOffscreenPixmaps" "true"
        Option "TexturedVideo" "on"
        Screen      0
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
        Option "XAANoOffscreenPixmaps" "true"
        Option "TexturedVideo" "on"
        Screen      1
EndSection

Section "DRI"
        Mode 0666
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

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
    
```

I have tried stripping down the xorg.conf file to only the bare minimum (basically removing the options from the "Device" sections) but it does not seem to make a difference. I am open to any and all suggestions. Thanks for taking the time to read all this if you're still with me here ;)

---

### Post by luisromangz on 2008-02-11
You need the AIGLX "on" option.

---

### Post by pormogo on 2008-02-12
Which section does that go under? The device section?

EDIT: I did some googling and found that it was supposed to go under the "Server Layout" section, that section now looks as follows 

[i]Section "ServerLayout"
# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        Option "AIGLX" "true"
EndSection[/i]

Still no dice same issue when trying to start compiz

[i]darthbator@superb-odifference:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e4a (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960
1024x768) to maximum 3D texture size (2048
2048): /usr/bin/compiz: line 229: [: too many arguments
/usr/bin/compiz: line 229: [: too many arguments
Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 1
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0[/i]

---

### Post by pormogo on 2008-02-12
I also tried checking fglrxinfo -v to make sure that the *" GLX_EXT_texture_from_pixmap"* function was available, and it seems to be.

[i]darthbator@superb-odifference:~$ fglrxinfo -v|grep "GLX_EXT_texture_from_pixmap"    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap[/i]

---

### Post by pormogo on 2008-02-12
Accidental double post

---

### Post by pormogo on 2008-02-12
This morning I tried using --indirect-rendering and --strict-binding to "force" AIGLX and I still got no dice. using the command 

*compiz.real --indirect-rendering --strict-binding --replace*

Causes X to crash, my display driver doesn't seem to be able to recover (the monitors hooked up to the box remain black). However service like ssh, smb, nfs, and DNLA still run perfectly... :( Reverting to my old config (that was single head and did not include the *Option "AIGLX" "true" * gives me a single monitor with functioning compiz. Does anyone happen to know if something about indirect rendering or compositing breaks when using a deal head ATI config (that sounds kinda out there and google doesn't seem to think it's broken in any way).

---

### Post by mrmiserable on 2008-02-12
Comparing resolution (1280x960
1024x76 to maximum 3D texture size (2048
204: /usr/bin/compiz: line 229: [: too many arguments
/usr/bin/compiz: line 229: [: too many arguments
Passed.

i know this says passed but i think you have your resolutions set to high for compiz to work i had same problem also the package amdccle is amd/ati catalyst control centre where you can adjust all settings here is my old xorg.conf maybe you can find something in this

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fr"
	Option	    "XkbVariant" "oss"
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

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "second Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 80.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "AllowGLXWithComposite" "true"
	Option	    "AccelMethod" "XAA"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1024x1024+1024x1024,0x0+0x0"
	Option	    "EnableMonitor" "tmds1,crt1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "2048x1024" "1280x1024" "1024x768"
	EndSubSection
EndSection
```

---

### Post by pormogo on 2008-02-13
Your old xorg.conf looks a lot like my old one the aticonfig tool generated the first time I ran it.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "CPD-E210"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"

#       Option      "GARTSize" "256"
#       Option      "AGPMode" "8"
#       Option      "ColorTiling" "on"
#       Option      "AccelMethod" "XAA"
#       Option      "EnablePageFlip" "on"
#       Option      "XAANoOffScreenPixMaps"
#       Option      "RenderAccel" "true"
        Identifier  "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
        Monitor    "CPD-E210"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

```

This works fine and produces compiz with the second monitor in mirroring mode. I can't see what's so different between this file and the other file that would cause compiz to break.

---

### Post by pormogo on 2008-02-13
So I reverted back to my --initial aticonfig generated xorg.conf file and paired it down a little and it's running compiz without any issues at all..... :(

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "AllowGLXWithComposite" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "Off"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "TexturedVideo" "on"
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

```

Very simple seems to be working very very well..... compiz runs perfectly. I tried playing around with the control center, and I don't think the word broken can even begin to explain what I found there. So I seem to be able to get compiz wokring as long as xorg is configured with only one monitor...... Adding a second monitor (and inherently a second device into the xorg.conf) seems to break compiz... The only thing I can think is there is a bug I haven't found documented yet, or I simply don't know how to add the second monitor and adapter well enough (and aticonfig is doing it incorrectly) to get compiz to work with a dual monitor setup.

---

### Post by mrmiserable on 2008-02-13
i changed this section and added 2048x1024 so then i reboot log in change desktop to this 2048x1024 in main menu/system/preferences/screen resolution and tick box to use make default

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "2048x1024" "1280x1024" "1024x768"
	EndSubSection
EndSection

might be the answer

---

### Post by pormogo on 2008-02-14
No dice :( I have no idea what's wrong with the dual monitor config. I don't even really know what to try next. Is there another forum where I should post this question? I was going to update my driver to the one released the other day, (I think on the 7th or 8th) but it doesn't seem to include any bugfixes that would cause me to think it would rectify my issue.

---

### Post by mrmiserable on 2008-02-14
have you done in terminal 

[HTML]aticonfig --query-monitor[/HTML]

and pairmode option (if you run just aticonfig in terminal you get a long list of options

also the xorg.conf i posted had pairmode 

Option	    "PairModes" "1024x1024+1024x1024,0x0+0x0"
Option	    "EnableMonitor" "tmds1,crt1"
Option	    "DesktopSetup" "horizontal"

yours does not i think this could help

good luck

---

