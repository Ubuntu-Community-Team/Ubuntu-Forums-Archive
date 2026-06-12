---
title: "WoW hanging up..."
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by ExSuSEusr on 2007-09-10
I've got WoW installed and can "start" it with Wine - no problems.

However, it hangs on the patching screen (with the Play button grayed out) saying:

> Downloading New Patch 16(kb)...

I spent the past couple of hours Googling this issue and have run into a few sites talking about it, but no one really offers an 'understandable' resolution.

I do have Gecko installed (obviously), Wine works well (seems to - at least with my other Win programs, Office, etc)... and again the install and original patch with WoW went smoothly.  It wasn't until everything was done and when I clicked on the desktop icon that it now hangs.

I surfed through WoW's official site, but they don't support Linux so I didn't find anything.

I am new to Ubuntu so please break it down if you have an idea of what I can do to get this working...

I have also downloaded and installed all the patches from the various mirrors.  It STILL hangs up.

Thanks much in advance!

---

### Post by ExSuSEusr on 2007-09-10
Manually downloading all the patches seemed to work...

But now instead of it hanging up on New Patch - it is hanging up on

Downloading Updated Tools....

This is really annoying.

---

### Post by derekr44 on 2007-09-10
Is this getting stuck on the "splash" launcher screen?  Just launch directly to WoW.exe and skip the news thing.

---

### Post by beeldings on 2007-09-10
What version of Wine are you using?

IIRC, one workaround for this problem is to launch "winecfg" from a terminal and set your Windows version to NT 4.0. Once your WoW installation is fully patched and updated, revert your Windows version back to Windows 2000 or Windows XP.

Also, are you running WoW in OpenGL or Direct3D?

---

### Post by ExSuSEusr on 2007-09-10
Hey guys, thanks for the replies.

Well, I tried just launching into WoW by the .exe instead of Launcher.exe&#8230; but when I do that it complete locks up the entire system to the point I have to actually manually hard power down the box.

I am using the latest version of wine for Ubuntu &#8220;Feisty.&#8221;  But, I&#8217;ll give the suggestion of changing to NT and installing the patch and then switching back to 2000.  

I am sure I will have some video issues when I actually get into the game, but at this point I can&#8217;t even log in.  Which is my main goal at the moment.  I think there is enough info out there to figure out those [video] problems when the time comes.  But, with this particular issue there just isn&#8217;t much out there in terms of &#8216;how to&#8217; fix.

So, again thanks for the input &#8211; any help is greatly appretiated.

You'll have to forgive my ignorance, because I don't know if I'm in OpenGL - I am pretty sure I am - or Direct3D... I am almost 90% sure I am in OpenGL.  But, would that cause my launcher to freeze while trying to install a small 300kb patch file?

---

### Post by derekr44 on 2007-09-10
> Well, I tried just launching into WoW by the .exe instead of Launcher.exe… but when I do that it complete locks up the entire system to the point I have to actually manually hard power down the box.

I'm pretty sure you might not have your 3d drivers working correctly.  What's your framerate on glxgears?

---

### Post by hikaricore on 2007-09-10
Just out of curiosity, why kind of video hardware do you have on your system?

And how did you go about installing the drivers for said hardware?

---

### Post by ExSuSEusr on 2007-09-10
My FPS with glxgears is roughly 280 or so.  3D rendering is enabled.  

I have a Radeon 9600.  I got the drivers from ATI's site and installed them through the terminal.

In the info it does say "ATI" and not "MESA."

Doom 3 runs smooths as glass too...

---

### Post by derekr44 on 2007-09-10
> My FPS with glxgears is roughly 280 or so.

That is very low.  You should be getting 9-10x that.

Plus if you've got the drivers loaded correctly, your xorg should reference "fglrx" instead of "ati" as the driver.

---

### Post by Stolen on 2007-09-10
glxgears is not a performance test. :)

I had the problem where it would lock up with the "downloading" message after I logged into wow.  I moved my Config.wtf out of the WTF dir, and I was able to log in and it passed the downloading stage.  I then logged out (where it locked again, so I killed the process) and moved my Config.wtf back into the WTF dir.  I can now log in and play, but I get a nice lock up on exiting WoW.

Only started seeing this with the latest version of wine (0.9.44)

I might downgrade a bit later on to see if that fixes everything.

---

### Post by derekr44 on 2007-09-10
It may not be a performance test, but it gives you a general idea.

---

### Post by ExSuSEusr on 2007-09-10
Ok, here's all the information I can think of that you might need to better help me with this proglem:

FPS - 

> ****@****:~$ glxgears
30825 frames in 5.0 seconds = 6164.943 FPS
42737 frames in 5.0 seconds = 8547.214 FPS
42754 frames in 5.0 seconds = 8550.699 FPS
42753 frames in 5.0 seconds = 8550.492 FPS
42755 frames in 5.0 seconds = 8550.877 FPS
42749 frames in 5.0 seconds = 8549.711 FPS

FGLRXFINFO -

> ****@****:~$ fglrxinfodisplay: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

Xorg info

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
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
	Identifier  "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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
	Device     "ATI Technologies Inc RV350 AP [Radeon 9600]"
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
	Option	    "Composite" "Disable"
EndSection 

Direct Rendering

> ****@****:~$ glxinfo | grep directdirect rendering: Yes

Here's a screen shot of what I am seeing when I try to start WoW:

[http://img401.imageshack.us/img401/5825/wowry1.jpg](http://img401.imageshack.us/img401/5825/wowry1.jpg)


Wine Version 0.9.33

Audio in Wine = OSS

I really would like to get this issue fixed... :(

---

### Post by Stolen on 2007-09-10
[http://www.codeweavers.com/compatibility/browse/name?app_id=1185;forum=1;msg=6583](http://www.codeweavers.com/compatibility/browse/name?app_id=1185;forum=1;msg=6583)

Might be an issue with that version of wine.

You can update to the latest released version (0.9.44) using these instructions:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

But like I've said, I've had some problems with this version and I'm going to try downgrading to 0.9.43.  In fact, I'm going to figure out how to do that right about now. :)

---

### Post by hikaricore on 2007-09-10
Sorry if you already tried this and I missed the mention of it, but have you run WoW.exe directly?

```
cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
wine WoW.exe -opengl
```

There is no reason for you to be running the launcher.

---

### Post by Stolen on 2007-09-10
Indeed, uninstalling 0.9.44 and manually installing 0.9.43 (using the .deb from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) ) fixed my freezing on close issue.

---

### Post by Stolen on 2007-09-10
and more of my unrelated to the OP's bug but still a hanging bug. :)

Wine does have an open bug for 0.9.44 with wow hanging on exit, should be fixed within the next release or two as patches fixing the issue have already been submitted.

[http://bugs.winehq.org/show_bug.cgi?id=9479](http://bugs.winehq.org/show_bug.cgi?id=9479)

---

### Post by ExSuSEusr on 2007-09-10
Ok changing Wine to 9.43 worked....

As suspected my frame rate is horrid, but something that should be an easy fix...

Thanks for all the help... I can finally log in!!

---

### Post by hikaricore on 2007-09-10
> **ExSuSEusr said:**
> Ok changing Wine to 9.43 worked....

As suspected my frame rate is horrid, but something that should be an easy fix...

Thanks for all the help... I can finally log in!!

If you hadn't seen the recent news, ATI is about to release better drivers (so they say).

So if nothing here fixes your issues, cross your fingers and hope for a the driver miracle that the community has been waiting years for to come true. :guitar:

---

