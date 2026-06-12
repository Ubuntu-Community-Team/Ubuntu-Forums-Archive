---
title: "AIGLX + compiz + ATI radeon"
date: 2006-11-18
forum: Desktop Environments
---

### Post by dmbeer on 2006-11-18
Hi All 

I have followed various threads and how to's on the forum and the web. None seem to help me get compiz working properly with Edgy.

I have and Ati Radeon X300SE fully support by the radeon driver. I have installed the packages available in the standard ubuntu repositories. 

My xorg.conf file looks like the following: 
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	BusID		"PCI:5:0:0"  
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option          "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

I am not sure what options I should use to get compiz to run. I know this works with my machine as I got it to work on FC6.

---

### Post by trogbot on 2006-11-18
The thread below relates to baryle & the livecd for Edgy, but it may help you.  The repo's it references needs to be put in the sources.list.  I followed it & all worked.  You should be able to do the same thing with a hard install.  Hope it helps.

[http://www.ubuntuforums.org/showthread.php?t=301364](http://www.ubuntuforums.org/showthread.php?t=301364)

Sorry, I don't know how to make links clickable on posts.:mrgreen:
Take that back, it is clickable.

---

### Post by dmbeer on 2006-11-18
I managed to get beryl working but not compiz from Edgy's main repository.

Any Suggestions? :-k

---

