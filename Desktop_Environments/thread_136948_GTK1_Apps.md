---
title: "GTK1 Apps"
date: 2006-02-27
forum: Desktop Environments
---

### Post by littlespy on 2006-02-27
How can I configure GTK 1 app themes to be a little cleaner?  Right now they have big ugly text, it seems to me that I just dont have a theme installed but I'm not sure how to configure everything properly.

---

### Post by cskeide on 2006-02-27
Try installing the following package:
gtk-theme-switch - GTK+ theme switching utility

```
sudo apt-get install gtk-theme-switch
```

Not sure what's installed by default, but there are different gtk-engines to choose from.

```
apt-cache search gtk-engines
gtk-engines-begtk - BeOS-like theme for GTK+
gtk-engines-eazel - The Eazel GTK+ theme engine, including the Crux theme
gtk-engines-geramik - Geramik GTK1.x Theme
gtk-engines-geramik-data - Geramik GTK Theme bitmaps
gtk-engines-icegradient - Ice-Gradient theme for GTK+
gtk-engines-industrial - Flat-looking GTK+ 1.x engine from Ximian
gtk-engines-lighthouseblue - LighthouseBlue theme for GTK+ 1.2
gtk-engines-metal - Metallic theme for GTK+ 1.2
gtk-engines-mist - A flat theme for GTK+ 1.2
gtk-engines-mono - Mono theme for GTK+ 1.2
gtk-engines-notif - Motif-like theme for GTK+ 1.2
gtk-engines-pixmap - Pixmap-based theme for GTK+ 1.2
gtk-engines-qtpixmap - QtPixmap GTK1.x theming engine
gtk-engines-raleigh - GTK+ 2.0-like theme for GTK+ 1.2
gtk-engines-redmond95 - Windows-like theme for GTK+ 1.2
gtk-engines-thingeramik - ThinGeramik GTK1.x Theme
gtk-engines-thingeramik-data - ThinGeramik GTK Theme bitmaps
gtk-engines-thinice - ThinIce theme for GTK+ 1.2
gtk-engines-xenophilia - Customisable GTK+ engine with a plain look

```

After installing gtk-theme-switch and your prefered gtk-engine, you should be able to switch themes by typing the following in a terminal:

```
switch
```

Let me know if this doesn't work. =)

---

### Post by littlespy on 2006-02-27
For some reason when I apply a theme using the switch interface, it doesn't stick.

---

### Post by NinjitsuStylee on 2006-05-25
This is a quasi-old thread but I figured I'd respond to this one because I was having the same issue.

When you run switch, it writes a line of code in the .gtkrc file that you should actually copy over to a new file in ~/ called .gtkrc.mine

So if .gtkrc looks like this:

```

# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/YOURTHEME/gtk/gtkrc"

include "/home/USERNAME/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

```

Then simply create a file in your home directory called .gtkrc.mine and copy/paste the line:

```

include "/usr/share/themes/YOURTHEME/gtk/gtkrc"

```

Where YOURTHEME is, of course, your theme, and USERNAME is your username.  It worked quite well for me! :)

---

### Post by ComplexNumber on 2006-05-25
use a theme that includes gtk 1 & 2 such as crux, bluecurve(*may* need to install the wonderland engine for this), digital-cream, etc

---

