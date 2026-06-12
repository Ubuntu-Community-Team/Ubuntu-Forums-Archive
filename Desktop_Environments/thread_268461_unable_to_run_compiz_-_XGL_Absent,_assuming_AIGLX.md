---
title: "unable to run compiz - XGL Absent, assuming AIGLX"
date: 2006-09-30
forum: Desktop Environments
---

### Post by tt101 on 2006-09-30
I have installed but unable to run compiz, getting the following error:

XGL Absent, assuming AIGLX
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0


How do I fix this problem?


I am running the nvidia driver with 2.6.15-23-386 kernel, as it doesn't work with the later versions.

Any help would be appreciated.

---

### Post by Sushi on 2006-09-30
What vid-card are you using? It seems that it doesn't support GLX_EXT_texture_from_pixmap which is needed for AIGLX. If you are using NVIDIA, their latest (still unreleased IIRC) drivers do support that extension.

EDIT: just saw that you are using NVIDIA. I think you have to wait for new drivers. Shouldn't be long though

---

### Post by siucdude on 2006-09-30
Also look into switching everything over to Beryl

---

### Post by Ramses de Norre on 2006-09-30
Are you trying to start an XGL or an AIGLX session?
As said before AIGLX is still a no go on nvidia, but XGL should definitely work.
And Beryl is indeed a lot better than compiz.

---

### Post by samssf on 2006-09-30
This happened to be as well after following some of the how-tos step by step. I doubt it has anything to do with your video card.

Follow the xgl+compiz how-to on the Ubuntu Guide. Make sure to modify the xorg and gdm-custom.conf files correctly.


This step is important... make sure your gdm-custom.conf says:

[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true



Also, you might have missed this step:


    * Find this section (your values may vary) 

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

    * Replace with the following lines, leaving the Identifier and BusID as it is 

Section "Device"
	...
	Driver		"nvidia"
	...
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection




I have severe problems but in the end this is what got me up and running. You might also try installing the compiz-vanilla packages instead of the regular ones... they are more stable. Good luck.

---

### Post by suhaib on 2006-10-29
I have also switched to beryl and am running beryl on edgy eft, but I get the absent message myself, althought it says that Nvidia is present.

---

### Post by hokutonoken on 2006-11-14
I have a Nvidia fx go5200 on an Acer aspire laptop.
I followed xgl+compiz how-to on the Ubuntu Guide and tried many times but I haven't managed to start an Xgl session.
Whenever I reboot in Xgl mode I get a black screen and the following error message

NVIDIA(0): Failure reading maximum pixel clock value for display device
NVIDIA(0): TV-0

Please note I correctly set the following lines:

in gdm.conf-custom

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true


and in xorg.conf

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"


Nvidia drivers are correctly installed and working 100%OK.

When I revert to default gdm.conf-custom, I get no warning message and x server starts correctly.. without xgl however, sadly.

Any advice?
Many thanks in advance

---

### Post by hokutonoken on 2006-11-14
Forgot to say I also disabled DRI module in xorg.conf, as suggested in Nvidia section of Xgl howto.
I don't have any Glcore module either.
I also have the module	"glx" correctly loaded in xorg.conf

I correctly set default depth to 24

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24


 I still can't get Xgl working.

NVIDIA(0): Failure reading maximum pixel clock value for display device
NVIDIA(0): TV-0

That's all I get.

Any suggestion?

---

