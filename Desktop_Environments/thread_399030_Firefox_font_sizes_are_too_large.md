---
title: "Firefox font sizes are too large"
date: 2007-04-01
forum: Desktop Environments
---

### Post by Kethinov on 2007-04-01
It seems like the default font sizes in Firefox are by default one size too large.

This is what Yahoo! looks like on a default Ubuntu install:

[IMG]http://eric.halo43.com/images/screenshots/2007-04-01-yahoo-ubuntu-default.png[/IMG]

----

This is what Yahoo! should look like, which I achieved by scaling down the font size by one:

[IMG]http://eric.halo43.com/images/screenshots/2007-04-01-yahoo-ubuntu-normal.png[/IMG]

This isn't the result of funky setting I've got in Ubuntu or anything. It's like this after a clean install as well.

---

### Post by nashira on 2007-04-28
If you check the settings in firefox under edit -> preferences -> content -> default font, the font size is set to 16, which is, in my opinion too big.  try 12, it seems to be a better choice.  Does anybody know why the default font size is so big in the first place?

---

### Post by fwojciec on 2007-04-29
Or you can do this...

Type the following into terminal:

> xdpyinfo | grep resolution

That will tell you what the actual DPI of your display is.  Put that value in System/Preferences/Fonts/Details and then adjust the font sizes in System/Preferences/Fonts.  That way Firefox fonts will always be the same size as the rest of the fonts on your system.

---

### Post by TheRingmaster on 2007-04-29
> **fwojciec said:**
> Or you can do this...

Type the following into terminal:



That will tell you what the actual DPI of your display is.  Put that value in System/Preferences/Fonts/Details and then adjust the font sizes in System/Preferences/Fonts.  That way Firefox fonts will always be the same size as the rest of the fonts on your system.

I got 87*96, which one is the dpi?

---

### Post by fwojciec on 2007-04-29
They are both - one is dots-per-inch horizontally, the other vertically.  To be honest I am not sure, on my computer I get something like 85x86 and I use 85.  Experiment,  you can always restore the settings to default.  I would try 87 dpi and see what it looks like.

---

### Post by fwojciec on 2007-04-29
There is also a more fancy way of solving that, by forcing DPI to 96x96 in xorg.conf, just in case anyone is interested.

For Nvidia this involves adding the following lines to the Device section 
> 	Option 		"UseEdidDpi"	"false"
	Option		"DPI"		"96 x 96"

(the first option disables automatic DPI detection, the second options, well, I don't think I need to explain the second one ;))

For other cards consult this [howto]("http://ubuntuforums.org/showthread.php?t=20976&highlight=cleartype") - just the part about setting the DPI which is at the beginning.  

That way font sizes will be uniform with the default 96 setting in Font preferences.

Make sure to backup xorg.conf before editing it!

---

