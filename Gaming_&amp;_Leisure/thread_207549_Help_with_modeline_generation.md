---
title: "Help with modeline generation"
date: 2006-07-02
forum: Gaming &amp; Leisure
---

### Post by kvonb on 2006-07-02
When I run a game like "Majesty" which uses a fullscreen mode, I get a "stepped" messed up picture.

I believe it is a modeline problem as my screen (as you can see below) is setup using DPMS.

From my xorg.conf:
-----------------------------------------------------------------
  Section "Monitor"
	  Identifier   "aticonfig-Monitor[0]"
	  Option	    "VendorName" "ATI Proprietary Driver"
	  Option	    "ModelName" "Generic Autodetecting Monitor"
	  Option	    "DPMS" "true"
  EndSection

  Section "Device"
	  Identifier  "aticonfig-Device[0]"
	  Driver      "fglrx"
	  Option	    "VideoOverlay" "on"
	  Option	    "OpenGLOverlay" "off"
          Option "UseInternalAGPGART" "no"
  EndSection
-----------------------------------------------------------------

My monitor is a Sony Multiscan G500, which supports quite high scanrates.

Any help and/or advice is greatly appreciated.

Regards,

Kev :)

---

### Post by kvonb on 2006-07-03
OK, after digging throught the dust covered remains of backed up configuration files, I managed to find the following modeline (which does work for me incidentally) if anyone is interested:

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option       "VendorName" "ATI Proprietary Driver"
	Option       "ModelName" "Generic Autodetecting Monitor"
	HorizSync    28.0 - 121.0
	VertRefresh  43.0 - 160.0
	ModeLine     "1600x1200@85" 83.9 1280 1312 1624 1656 800 816 824 841
	Option       "DPMS" "true"
EndSection
```

I have no idea what the numbers mean, please post if you have the required knowledge so that I and others can learn.

I changed the "1600x1200@85" part from the original "1280x1024@60" and it now gives me a default resolution of 2048x1536@75hz which makes no sense to me!

Regards,  Kev :)

---

