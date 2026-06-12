---
title: "KDE Crystal Icons on Gnome"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by LordKelvan on 2007-06-21
Hi:

I am currently using Ubuntu (and consequently also using gnome).  While I like gnome, and am pretty comfortable with it, I really love the default KDE icons (I love how "bubbly" and bright they are).  There are a couple crystal icon packs that try to port KDE icons to gnome, but they are incomplete ports.  People keep pointing to crystalgnome.org, but I haven't been able to successfully login (I am registered though).

Does anyone know of complete ports of the KDE crystal icons to gnome, and where I might get them?

As well, can someone tell me where in gnome are all the icons specified (i.e. the file that gnome uses to determine which icon to use for what) so that I can tweak icon themes/sets further to my liking?

Thanks in advance,
LK

---

### Post by LordKelvan on 2007-06-23
Anyone?

---

### Post by BobCFC on 2007-06-24
when I install an icon set it puts it in a hidden folder in the home directory called .icons

press Crtl-H to view hidden files or use the View menu.   I can then replace icons in this folder to customise my desktop.   Note that icons with the shortcut arrow are symlinks to prevent duplication so replace the original without an arrow and they will all follow.

---

### Post by LordKelvan on 2007-06-24
Hi:

Yep - I see the icon folder.   But there seem to be certain things on my system which the icon theme did not replace (I will assume that means it doesn't have its own icon for that thing, so gnome just uses the default).  What I want to know is where does gnome look for its icons?  Like how does it know that for element X I should look at location Y, and if I can't find it, then I should use default  Z?  

Cheers,
LK

---

### Post by avik on 2007-06-24
Icons are also stored in /usr/share/icons, so you'll want to look there next for the names of the icons.  Once you find the names, place the corresponding Crystal icons in the icon folder where you looked before (the one in the home directory).

---

### Post by LordKelvan on 2007-06-24
Hi:

There is a problem with the approaches being given (CAPS is for emphasis not anger) - they are useful only if I wanted to CHANGE an existing icon in the theme.  They however don't work if a particular theme is MISSING an icon altogether - in that case, I can't exactly go look for one.

It would be really helpful if someone could tell me where gnome looks to determine what icon to use.  For example, lets say that I find an icon called gnome_startup_button.png, how does gnome know to use that icon for the startup button?  Is this choice hardcoded (in which case it would be helpful if someone could point me to a place that lists this hard-coded naming scheme), or does gnome read a configuration file somewhere (in which case could someone tell me where that is)? 

Thanks,
LK

---

### Post by kpolice on 2007-06-25
It is in the source code of the application.

First it looks in you icon theme, next in any icon theme that the one you are using inherits. If it can't find the icons there it goes to the default theme and also to /usr/share/icons/hicolor .

Some apps use the stock gtk icons and newer apps also follow the freedesktop icon naming spec.
[http://developer.gnome.org/doc/API/2.0/gtk/gtk-Stock-Items.html](http://developer.gnome.org/doc/API/2.0/gtk/gtk-Stock-Items.html)
[http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html)

Just take the gnome icon theme as a template.

---

### Post by LordKelvan on 2007-06-25
Thanks for the info - I will take a look into those links.

---

