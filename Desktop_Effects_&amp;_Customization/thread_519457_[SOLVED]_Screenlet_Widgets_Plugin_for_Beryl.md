---
title: "[SOLVED] Screenlet Widgets Plugin for Beryl"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by pofigster on 2007-08-07
Howdy!

I installed the screenlets app and then I read about a way to get them to act like widgets in OS X.  I looked around and found some code that's supposed to do it in Beryl (which I am running at the most current version for Feisty).

The code is at: [http://forum.beryl-project.org/viewtopic.php?f=38&t=2554]("http://forum.beryl-project.org/viewtopic.php?f=38&t=2554")

I made sure I had the necessary development packages installed (as best as I can tell) and this is the result I get when I try to compile the source code:

> $ sudo make
compiling : widget.c -> build/libwidget.lowidget.c:474: warning: type defaults to 'int' in declaration of 'CompTransform'
widget.c:474: error: expected ';', ',' or ')' before '*' token
widget.c: In function 'widgetInitScreen':
widget.c:1016: error: 'widgetPaintWindow' undeclared (first use in this function)
widget.c:1016: error: (Each undeclared identifier is reported only once
widget.c:1016: error: for each function it appears in.)
make: *** [build/libwidget.lo] Error 1


Any ideas on what went wrong or how I can fix this?  Thanks!

PS - I did try and post about this on the appropriate Beryl forum, but their system wouldn't let me create a new account - said it was closed to requests.  Anyway, this is the best community, so I figured I could get some help here.

---

### Post by dcotruta on 2007-08-07
I got this to work in the following way.

Tried compiling the Widgets Beryl plugin from source and that crashed (different error message from yours).

I then went to [http://forum.beryl-project.org/viewtopic.php?f=38&t=2554]("http://forum.beryl-project.org/viewtopic.php?f=38&t=2554"), which is all about the Widget plugin.

I knew that the screenlets were working, so all I had to do was remove my existing beryl-plugins deb (from synaptic). I also removed beryl-plugins-data. Beryl, beryl-manager & beryl-settings were automatically removed (although beryl-core isn't).

I then downloaded Trevino's plugin deb from his site: [http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/]("http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/").

I installed that deb manually, ignoring the warning about newer versions. I then reinstalled beryl manually from synaptic (which will also reinstall beryl-manager & beryl-settings [although it should be noted, when I did uninstall beryl it didn't stop working in the current session].

Note, I did not install the plugin-data deb from Trevino - I simply reinstalled the one from synaptic. It all seems to work and that way I only have one package out of date. If you run into any problems, it may be because you need that package-data file too. I'm not entirely sure what it does. 

Finally, if all else fails, try building beryl completely from Trevino's debs.

When all was said and done, I had a Widget Layer box in the Beryl Settings Manager, under Desktop. I enabled this, opened a screenlet and right clicked inside it from the Window menu I selected Widget and the screenlet dissapeared. I then hit Super + F9 (the default hotkey for the "Dashboard") and there were the screenlets in all their glory.

BTW - I'm doing this on an ATI card, using the fglrx driver & XGL.

---

### Post by pofigster on 2007-08-07
Thanks!  I'll give it a try!

---

### Post by firefeather on 2008-06-09
I know that the recent versions of Screenlets are already configured to be able to do this by right-clicking the screenlet and then checking "Widget" under the "Window" menu. No widget layer plugin configuration required. However, I am not so sure it works on Beryl. I do know it works on compiz fusion.

---

