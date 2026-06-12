---
title: "Newbie questions"
date: 2005-08-08
forum: Desktop Environments
---

### Post by seethru on 2005-08-08
Hello all, I've recently made the switch to linux, and chose Ubuntu as my distro. I'm enjoying it so far save for a few problems.

1. Nforce Audio: I managed to get the drivers installed, but I have yet to get the sound working. I read the release notes, and I have no idea where to put anything they speak of.

> 
Other distributions
If the distribution you are using provides a configuration mechanism for audio drivers, use it to select the nvsound driver module for use with the nForce audio device. Otherwise, manually edit the module configuration file.

If your configuration file already contains an entry for the i810_audio, snd-intel8x0, or nvaudio drivers (open-source audio drivers that supports the nForce audio controller), that entry needs to be commented out with a # or removed:

# alias sound-slot-0 i810_audio

Add the following line to the configuration file:

alias sound-slot-0 nvsound

On some distributions, you may need to replace sound-slot-0 with snd-card-0.

If you wish to have nvmixer audio settings automatically restored each time the nvsound driver loads, add the following lines to the configuration file for 2.4 kernels:

post-install nvsound sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 ||:
pre-remove nvsound /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 ||:

For 2.6 kernels:

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound

For both 2.4 and 2.6 kernels, you should also edit /etc/rc.d/init.d/halt, or /etc/init.d/halt.local on SuSE distributions:

if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
/usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1
fi


2. Nvidia Video Drivers: I used apt-get to install them, although I think I'm going to install the newer ones from the website. I was hoping getting the drivers installed would get my refresh rate problem fixed, however it didn't. Also when I try to run sudo nvidia-glx-config enable I get...

> 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Here is my xconf.org file, I'm not sure why the refresh rates aren't working, my only option is 60hz and it's killing my eyes.

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Option		"DPMS"
	HorizSync	30.0-85.0
	VertRefresh	50.0-160.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"SAMSUNG"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Thanks in advance, if I can get this all worked out I'll be very happy with my switch.

---

### Post by Lord Illidan on 2005-08-08
Yeah on Debian Sarge, with the same hardware I am running at a nice 71 Hz, which is good for my eyes and quite relaxing! 
In Kubuntu, the 60 Hz is ugly and gives u a head ache...

---

### Post by seethru on 2005-08-08
anyone? I can't get my sound working, or my refresh rate higher than 60, for the life of me. I've tried searching, tried a bunch of different ways, and none seem to be working.

---

