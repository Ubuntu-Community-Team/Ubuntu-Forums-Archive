---
title: "Screen Resolution"
date: 2009-06-10
forum: Desktop Environments
---

### Post by cochran242 on 2009-06-10
I am having a problem with my screen resolution. I have a Dell D630 laptop. When docked I have 2 external monitors, one DVI and one VGA that use the Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller. Every time X11 starts I have to go into System-Preferences-Display and then I have to change something (I usually change the refresh rate) in order for the VGA monitor to start displaying. I can live with it but I am hoping for something a bit more seamless. Even a script that will detect connected monitors and adjust the settings would work for me too. Thanks.

---

### Post by cochran242 on 2009-06-11
As an alternative question too, is there any other screen managers that would work better?

---

### Post by densou on 2009-06-11
you have no choice: [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)
[http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

advice: into your Xorg.conf edit first two lines of *Section  "Device"* into

```

	Identifier 	"intel"
	Driver 		"intel"

```

(I am not aware if xrandr -with GUI- works better or worse, it's called *grandr*)

---

