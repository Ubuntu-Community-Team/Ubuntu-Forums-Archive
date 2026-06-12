---
title: "Robb\Hotcorners Error - Beryl Won't Load"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by goofeyfoot on 2007-09-19
This error has been driving me nuts for a week.

I have set up the Nvidia Drivers

I am using Feisty.  AMD machine.  Asus MB

When I install Beryl and Emerald they install fine.  But Beryl never loads.

Running Beryl in a terminal window ends with an error.  The text is shown bellow.

When you try to run Beryl as the application of choice, your selection in the drop down box doesn't "take".  It reverts to a default manager every time.

Here is the total printout from the terminal window.  Note the /robb/hotcorners reference at the end.

Detected xserver : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : passed
Checking maximum texture size : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : passed
Checking maximum texture size : passed (4096x4096)

[I]Reloading options
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
Segmentation fault (core dumped)
michael@michael-desktop:~$[/I]

To make matters worse, there is no "robb" file or any "hotcorners" file I can find anywhere in the file system.  So I have no idea what they are.

As a newbie, I also don't know what is calling these non-existent paths up.  Nor do I know how to figure out what is calling them up.

And believe me, I have deleted and reinstalled Beryl and Emerald half a dozen times with no luck.  It's never the easy fix that works, right?

Has someone ever run into this problem?  Does anyone know how to fix it?

Like I said I'm going nuts.  The voices in my head again...  The aliens are here...Woe is me!

Thanks 

Michael

---

