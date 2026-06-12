---
title: "Title Bar disappers, can't move windows..."
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by ryanlhjess on 2007-11-02
I have a dual monitor setup with an nvidia 6600GT on Ubuntu 7.10, I have seem to have lost the 'title bar on top of my window (the bar to click to drag windows around) and now i can't move around my windows.

Please help me fix this problem!

---

### Post by Kamilion on 2007-11-02
Howdy. Had the same problem. You'll have to edit your xorg.conf.

Check my post on how I fixed it:
[http://ubuntuforums.org/showpost.php?p=3646530&postcount=2](http://ubuntuforums.org/showpost.php?p=3646530&postcount=2)

These need to be added to "Device"
```

	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"

```
These need to be added to "Screen"
```

	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"RenderAccel"		"True"

```
And you need to add this section to the end:
```

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

That should fix you up.

---

### Post by ryanlhjess on 2007-11-02
how do i get write access to the /etc/x11 ?

---

### Post by Whiffle on 2007-11-02
sudo gedit /etc/X11/xorg.conf

---

### Post by ryanlhjess on 2007-11-08
its just empty?

---

### Post by mtngun on 2007-11-08
I'm having the same problem, and the suggested change to xorg.conf didn't solve the problem on my machine.

I can move the program on the screen by ALT + left click and hold anywhere on program + drag.

The minimize button is missing, too, but I can minimize with ALT F9.

Ditto for maximize, ALT F10.

Ditto for close, ALT F4.

However, I miss the graphical commands.  I'll keep lurking on this forum for a few more days, looking for a fix.  If all else fails, I'll unistall compiz.

---

### Post by mtngun on 2007-11-09
My title bars are back !!!!   

:guitar:

This is what happened.  I lost the title bars while playing around with themes and effects.  I didn't notice exactly when they disappeared, so I had no way to retrace my steps.

I tried all the suggestions posted on this and other threads, to no avail.

Today I went to System>Appearance>Visual Effects and changed from "custom" to "extra."  The title bars instantly returned.   

But I no longer had the infamous cube.  No big deal.  It's mostly for show, anyway.

Nonetheless, I tried turning the cube and rotate cube back on.   Now I have the cube plus I still have the title bar.  Awesome.

---

