---
title: "1080p Resolution in Ubuntu"
date: 2010-07-19
forum: Desktop Environments
---

### Post by raisdead on 2010-07-19
I am having problems displaying gnome at the highest resolution for my monitor 1080p or 1920x1080. I currently have 1280x1024 resolution removing splash and add nomodeset to the kernel line in grub2.



Results from xrandr:

Screen 0: minimum 1024 x 768, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      61.0* 
   1024x768       61.0  



results from get-edid | parse-edid:
	# EDID version 1 revision 4
Section "Monitor"
	# Block type: 2:0 3:fc
	Identifier "Sony LCD"
	VendorName "MS_"
	ModelName "Sony LCD"
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 43-66
	VertRefresh 39-61
	# Max dot clock (video bandwidth) 170 MHz
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x1080"	# vfreq 59.940Hz, hfreq 65.635kHz
		DotClock	162.840000
		HTimings	1920 1952 1984 2481
		VTimings	1080 1083 1086 1095
		Flags	"-HSync" "-VSync"
	EndMode
	Mode 	"1920x1080"	# vfreq 40.001Hz, hfreq 43.801kHz
		DotClock	99.910000
		HTimings	1920 1952 1984 2281
		VTimings	1080 1083 1086 1095
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection




Any help would appreciated. 
Thanks

---

### Post by raisdead on 2010-07-22
Could it be something dealing with my Intel GM45 graphics driver? In addition scrolling and moving windows does not seam "fluid" it appears to be jumpy.

---

