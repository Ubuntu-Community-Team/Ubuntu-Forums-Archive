---
title: "See if you can figure this one out guys and gals (New Reso. Isssue, Heavily searched)"
date: 2005-07-11
forum: Desktop Environments
---

### Post by ImaMadGoat on 2005-07-11
Alright, I know you have all seen the numerous posts about fixing resolution and believe me I have searched and applied them all. I have a new problem that I'd like to see someone take a crack at cause I'm stumped. Keep in mind I'm new to Linux but I'm a quick study. 

Setting the stage:

In Windows, I was capable of achieving a resolution of 1280x1024 @ 60htz. I could also, and primarily used a resolution of 1152x864 @75htz. When I would use my monitor controls on the front of the monitor (HP 7500), it would display the resolution and refresh rate I was using. So if I had my res set to 1024x768 at 85htz, the monitor would display that on it's menu. What was odd was when (using windows) I had my resolution of 1152x864 at 75htz, the monitor display would say 'user mode' instead of displaying the current resolution. My thinking behind this was I never actually installed the HP 7500 driver in windows. I used the plug and play standard driver.

In linux

I have correctly configured the xorg xserver to give me the following resolutions. 640x400, 800x600, 1024x768 all at 85htz. I can also achieve 1600x1200 and 1280x1024 at 60htz. But as you know I wanted 1152x864 at 75htz. So I did what all the posts said to do which is manually edit my xorg file. Here is a copy of the xorg.conf file (the relevant portion anyway). If you see anything in here that doesn't look right, inform me. Again I am trying to acheive a resolution of 1152x864 at 75htz. I know the monitor is capable of doing it. 

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	96000
EndSection

Section "Monitor"
	Identifier	"hp 7500"
	Option		"DPMS"
	HorizSync 30-70
	VertRefresh 50-140
	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
  	Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"hp 7500"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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

Help me figure this one out guys. All the settings for the monitor are correct.

Thanks
The Goat

---

### Post by az on 2005-07-11
CTRL-ALT-F1
log in
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
(Be sure to enter you desired resolutions in the table)
sudo /etc/init.d/gdm start

---

### Post by ImaMadGoat on 2005-07-11
Azz, doing what you said ends up deleting the horisyc and vertrefresh entries right from my xor.conf file. It detected my monitor, as it has done before, and I entered the correct refresh rate ranges as I did before. I selected the resolutions that I wanted. When I restarted. All I have is 640x480 and I have to manually edit the file to bring me back to my original 1024x768 resolution.

Any other ideas or takers out there?

---

