---
title: "poor performance with Latitude XT, Radeon, Orientation right"
date: 2010-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bastie87 on 2010-04-18
Hi,

finally, after getting touch, pen, etc. working,

I noticed a real poor performance in gnome when rotating screen right with xrandr.

(Redrawing of windows is really slow)

Is there any solution for that?

```

Section "Device"
	Option	    "DynamicPM" "on"
	Option	    "ClockGating" "on"
	Option	    "AccelMethod" "EXA"
        Option     "EnablePageFlip" "true"    	# [<bool>]
        Option     "DMAForXv" "true"          	# [<bool>]
        Option     "AccelDFS" "true"          	# [<bool>]
        Option     "RenderAccel" "true"       	# [<bool>]
        Option     "DRI" "true"                	# [<bool>]
        Option     "EXAVSync" "true"           	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Xpress 1250"
	BusID       "PCI:1:5:0"
	Option		"RandRRotation"  "on"
EndSection

```

---

