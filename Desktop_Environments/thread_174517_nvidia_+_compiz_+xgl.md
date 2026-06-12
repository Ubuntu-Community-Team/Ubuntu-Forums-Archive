---
title: "nvidia + compiz +xgl"
date: 2006-05-11
forum: Desktop Environments
---

### Post by p47 on 2006-05-11
Hello I have a problem with compiz and xgl I hope you can help me !

I have all the instaled in my pc but I can't see any efects...
I read two howto's and I still having problems...

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)
[https://wiki.ubuntu.com/QuinnsXglAndCompizHowto?highlight=%28compiz%29](https://wiki.ubuntu.com/QuinnsXglAndCompizHowto?highlight=%28compiz%29)

I was reinstaled all but I have the same problem.
When I want to run compiz I have problems the windows don't has up bar and I can't move all the window that was open...
I can't see any efects .

I have this in /gdm.conf-custom

[servers]
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer -kb
flexible=

and in /gdm.conf

# will be the display number of that server.  Usually just the 0 server is
# used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on Linux and FreeBSD.  Don't add any
# vt<number> arguments if VTAllocation is on, and set FirstVT to be the first


in xorg.conf I have this:

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

and in the last part I add this 

Section "Extensions"
	Option  "Composite" "Enable"
EndSection

I don't know what is the problem
my order in gconf is this...

gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

Kind Regards !
Thank's

---

