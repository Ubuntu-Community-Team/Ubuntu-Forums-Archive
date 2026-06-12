---
title: "Monitor Problem"
date: 2008-12-04
forum: General Help
---

### Post by ghostmunch on 2008-12-04
Here's the story.

I bought an X2gen (model MW20T) lcd monitor.

It works but when I first booted up when the login screen was supposed to come up 
there was instead a black screen with a blue square that had text that read
"frequency out of range". 

I researched online and found some info about it that did help some.

I edited xorg.conf with the information that I got.

Here's the edit.
------------------------------------------------------------------------------
Section "Monitor"
	Identifier	"Generic Monitor"
	ModelName	"MW20T"
	Option		"DPMS"
	Horizsync	30-82
	Vertrefresh	56-76
EndSection


Section "Screen"
	Identifier	"Default Screen"
        Device          "nVidia Corporation GeForce 6100 nForce 430"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"metamodes" "1680x1050 +0+0; 1440x900_75 +0+0; 1024x768 +0+0; 800x600 +0+0"
# Commented most of the following because of the above metamode. Still get "Out of Sync" if I don't. >_>
#	SubSection "Display"
#		Depth	16
#		Modes		"1440x900"	"1024x768"	"800x600"
#	EndSubSection
	SubSection "Display"
		Depth	24
#		Modes		"1440x900"	"1024x768"	"800x600"
	EndSubSection
EndSection
------------------------------------------------------------------------------


The monitor and screen sections are the only sections that I changed.

Now the monitor works for everything (internet, text editor, so on.) except games. 
Any games opened send the monitor back to the warning saying "frequency out of range".
------------------------------------------------------------------------
Possibly applicable information.

Monitor:
X2gen MW20T

The computer being used with the monitor:
Ubuntu release 8.04
Kernel Linux 2.6.24-22-generic
Gnome 2.22.3

Memory: 1.8 GiB
Processor AMD Athlon Processor LE-1600

Graphics processor:
GeForce 6150SE nForce 430
------------------------------------------------------------------------

What can I change in the xorg.conf to make the monitor work on everything.

I could go and get a new monitor, but I am so close to getting this one to work I thought I would keep trying. I really would appreciate the help.

---

### Post by ghostmunch on 2008-12-04
[http://ubuntuforums.org/showthread.php?t=788560&highlight=x2gen+monitor+problem]("http://ubuntuforums.org/showthread.php?t=788560&highlight=x2gen+monitor+problem")

The above url is on the same subject as this thread.

---

### Post by ghostmunch on 2008-12-04
I tried the next link.

[http://ubuntuforums.org/showthread.php?t=302303&highlight=x2gen+monitor+problem](http://ubuntuforums.org/showthread.php?t=302303&highlight=x2gen+monitor+problem)

With this command: ```
sudo ddcprobe | grep monitorrange
```
my monitor just blacks out for a second.
--------------------------------------------------------------------------------
With this command: ```
sudo ddcprobe
```
I get this output.

vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: MCP61 - mcp61-80 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

---

### Post by ghostmunch on 2008-12-04
[http://ubuntuforums.org/showthread.php?t=492850&highlight=x2gen+monitor+problem](http://ubuntuforums.org/showthread.php?t=492850&highlight=x2gen+monitor+problem)

The person who posted this link received similar output from using
```
 sudo ddcprobe
```

---

### Post by CatKiller on 2008-12-04
> **ghostmunch said:**
> Now the monitor works for everything (internet, text editor, so on.) except games. 
Any games opened send the monitor back to the warning saying "frequency out of range".

It sounds like you've got your games set up using a resolution/refresh rate combination that your monitor doesn't want to handle. You either want to get those games to use the resolution that works on the desktop or get the resolutions that your games are using to use a refresh rate that your monitor will do.

I don't know if xorg.conf Options are case-sensitive or not, but you might try HorizSync and VertRefresh instead. You might also want to have ```
        Option          "UseEDID"                       "False"
``` in your "Device" section to tell X to use the refresh rates that you've specified rather than what the graphics driver reports that your monitor can do.

---

### Post by ghostmunch on 2008-12-04
I will try that.

---

### Post by ghostmunch on 2008-12-04
Thank you CatKiller!

That did it.

I played Astromenace and Secret Maryo Cronicles fine.

This problem had almost driven me to buy a different monitor. Good thing I held out.

The X2gen company no longer exists, and on another thread in some other forum(maybe here - I was looking fast) someone advised to just forget about the cheap monitor and put the cash forward for a more expensive one. Now my cheap purchase works.

---

