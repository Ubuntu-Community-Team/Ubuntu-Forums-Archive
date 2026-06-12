---
title: "Dual Monitors, ATI &amp; Beryl Running Compiz"
date: 2007-05-09
forum: Desktop Environments
---

### Post by voodoochild on 2007-05-09
Hi all,

My first post.... in week 4 of my virgin ubuntu relationship and my first call for assistance, though admittedly this is all about eye candy, nothing essential....

I have come to terms with not being able to run beryl / xgl on my 2560x1024 dual head setup (that whole max texture 2048x2048 shebang) so i thought  would have a wee mess around with beryl running compiz. 

I have an ATI Radeon 9200, and have my dual head set up in xorg.conf using the ATI Screen 0 / Screen 1 method.

Screenshots below:
[B]
Metacity[/B]
[IMG]http://www.visperas.co.uk/metacity.png[/IMG]

**Compiz**
[IMG]http://www.visperas.co.uk/compiz.png[/IMG]

As you can see, compiz is running on that small section of screen 0 perfectly (all effects, or rather what i can see of them, seem to be just fine), but that is all i get... (god knows how my screensaver got into the buffer to take up the rest of the workspace). This leads me to harbour the ambitous hope that i can make it work on both....



Has anyone any ideas? I will love you all forever.....

Luke

---

### Post by Eddie Hung on 2007-05-09
Doesn't the 2048x2048 texture limit apply also to compiz too?

Or is it clever in that it only applies itself to screen 0, rather than the whole thing like beryl tries to do (and fails?)

Eddie

---

### Post by voodoochild on 2007-05-10
Brainwave.... 

Running Beryl Manager through Terminal with beryl confirms the 2048x2048 crash, and doesn't even get started, falling straight back to metacity. 

With Compiz i get the following dialogue:

> /usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
inotify_add_watch: No such file or directory
X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.


Does that help at all?

---

### Post by Eddie Hung on 2007-05-11
I'm not following, sorry.

Just to clarify, I'm also a ATI owner (x800 - which isn't fully supported by the open source drivers, therefore I use the propietary fglrx) with two monitors - so I'm very much in the same boat as you.

My monitors, when set to display side by side as they are on my desk, exceeds the 2048 width when running MergedFB (Xinerama) and therefore beryl refuses to run, when using open source drivers (running in terminal shows that it does not pass the max texture size test)

When not merging the monitors and doing dual head, and using open source drivers, DRI is automatically disabled, so beryl refuses to run.

Switching over to fglrx, I needed to run XGL in order to get beryl to work. I did not merge the screens (otherwise I would run into the 2048 limit again), but left it as dual head, and then eventually succeeded in launching one XGL server for each monitor, and running beryl again on each - although this is not really a permanent solution as the same gnome session is launched in each and look a bit wonky as the screen resolutions are also different, but it does run!

I'm confused as to what you're trying to do though - surely compiz would run into the same problems?

Care to elaborate?

Eddie

---

