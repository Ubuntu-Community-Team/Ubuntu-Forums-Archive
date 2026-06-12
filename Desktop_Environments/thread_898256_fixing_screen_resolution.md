---
title: "fixing screen resolution"
date: 2008-08-23
forum: Desktop Environments
---

### Post by orrorin on 2008-08-23
First, here's my problem ...

I connect to my Ubuntu Hardy 8.04 64bit, using a KVM switch. Unfortunately, if I'm currently logged on some other machine through the KVM and boot up the Ubuntu machine, then since the Ubuntu machine is not under KVM focus, it ends up with horrendously low screen resolutions (800x600 instead of 1920x1200).

So, I tried to hard-code the resolutions in my xorg.conf, but that does not seem to help for some reason. Here's what my xorg.conf looks like ...

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
# 1920x1200 @ 50.00 Hz (GTF) hsync: 61.75 kHz; pclk: 158.08 MHz
	Modeline "1920x1200_50"  158.08  1920 2032 2240 2560  1200 1201 1204 1235  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection  "Display"
	Modes "1920x1200_50"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

It's essentially the default xorg.conf with Modelines added, which were obtained using gtf.

Can someone pl. identify what could be wrong with it? I'm still not getting the higher resolution, unless the KVM focus is on the Ubuntu machine? Looks like Ubuntu is querying the display and the KVM responds with some default values. I understand that the real problem is with the KVM, but IOGear has washed its hands off this.

---

### Post by kagashe on 2008-08-23
Use this command to get the available resolutions:
> $ xrandr -q
If the above command shows that 1920x1200 is available you can change with the following command:
> $ xrandr --output VGA0 --mode 1920x1200

kagashe

---

### Post by cyrilmethodius on 2008-08-23
I know this is a common question but I have the same problem.   I tried everything I could think of and most of the things on this page: 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
But, it seems nothing changes the two selections I see in preferences.   

I have a rather old eMachine monitor (eView 171).   Has anybody else been able to find the "magic" settings for this monitor?  Is it more to do with the video card or the monitor itself?

---

### Post by kagashe on 2008-08-23
> **cyrilmethodius said:**
> I know this is a common question but I have the same problem.   I tried everything I could think of and most of the things on this page: 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
But, it seems nothing changes the two selections I see in preferences.   

I have a rather old eMachine monitor (eView 171).   Has anybody else been able to find the "magic" settings for this monitor?  Is it more to do with the video card or the monitor itself?This page is mostly obsolete since dpkg-reconfigure xserver-xorg no longer works on Ubuntu Hardy.

RandR 1.2 was introduced in Gutsy and it is supposed to be used to change resolution in Gutsy and Hardy. Try to use the command as suggested by me in previous post.

kagashe

---

### Post by orrorin on 2008-08-23
> **kagashe said:**
> Use this command to get the available resolutions:

If the above command shows that 1920x1200 is available you can change with the following command:


kagashe

Thanks for the reply kagashe, but it does not seem to fix the problem. If I boot my Hardy in the background while focusing on another machine thru the KVM, then Hardy still ends up with low resolutions.

Basically, what I want is when Hardy-64 is booting up, it should not query for display properties and instead use the hardcoded resolutions.

---

### Post by kagashe on 2008-08-23
> **orrorin said:**
> Thanks for the reply kagashe, but it does not seem to fix the problem. If I boot my Hardy in the background while focusing on another machine thru the KVM, then Hardy still ends up with low resolutions.

Basically, what I want is when Hardy-64 is booting up, it should not query for display properties and instead use the hardcoded resolutions.ok. Please read Section III. xorg.conf based configuration on [this page]("http://wiki.debian.org/XStrikeForce/HowToRandR12").

kagashe

---

### Post by cyrilmethodius on 2008-08-23
Kagashe - Thanks for all the help.   Actually, shortly after chiming in with the problem I was having, I did some exploring thru System->Administration->Hardware Drivers.  There was a message there that said that nvidia was disabled and that I could not do games without it.   I don't use games anyhow but I thought I may as well enable it and see what happens....sure enough, as soon as I did, my default 1024 resolution came up!   Call me "luck beginner."

---

