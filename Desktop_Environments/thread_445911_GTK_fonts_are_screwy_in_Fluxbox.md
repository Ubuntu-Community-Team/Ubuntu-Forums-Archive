---
title: "GTK fonts are screwy in Fluxbox"
date: 2007-05-16
forum: Desktop Environments
---

### Post by anti-dan on 2007-05-16
Hi, I am having trouble getting my GTK fonts to display correctly. The fonts are fine in GTK2 programmes but come out as some sort of pre-defined rubbish font in GTK1 programmes (xmms, audacity, whatever). I've used gtk-theme-switch to specify a font (I have gone for "clean") but to no avail. As you can see in the screenshot below, the same font works for the fluxbox title bar, but the main window is all odd:

[IMG]http://i5.photobucket.com/albums/y188/drunkndisorderly/screwy-audacity.png[/IMG]

Help!

---

### Post by kerry_s on 2007-05-16
Use a .gtkrc-2.0 put> gtk-font-name="verdana 10"
Change font & size to your likeing

---

### Post by hyperair on 2007-05-16
[quote=kerry_s]Use a .gtkrc-2.0 put> gtk-font-name="verdana 10"
Change font & size to your likeing[/quote]
Could you reiterate your instructions in a clearer method? I've been with Ubuntu since the release of Dapper and even I don't understand what you just put there.

---

### Post by Viskovitz on 2007-05-16
Maybe he meant something like this:

[https://help.ubuntu.com/community/Gtk1Fonts](https://help.ubuntu.com/community/Gtk1Fonts)

---

### Post by anti-dan on 2007-05-16
> **kerry_s said:**
> Use a .gtkrc-2.0 put> gtk-font-name="verdana 10"
Change font & size to your likeing

My GTK 2 fonts are alright though. I tried the above thinking maybe gtkrc-2.0 had an effect on GTK 1 programmes but no joy.:confused:

Here are my gtkrc files:

**.gtkrc**
```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/3000_xeno/gtk/gtkrc"

style "user-font"
{
  font="-schumacher-clean-medium-r-normal-*-*-120-*-*-c-*-koi8-r"
}
widget_class "*" style "user-font"

include "/home/daniel/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

**.gtkrc-2.0**
```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/IndustrialTango/gtk-2.0/gtkrc"

style "user-font"
{
  font_name="Sans 8"
}
widget_class "*" style "user-font"

include "/home/daniel/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

**.gtkrc-2.0.mine**
```
gtk-font-name="verdana 10"
```

Any clue? Thanks for the help :)

---

### Post by Viskovitz on 2007-05-16
Maybe you should erase everything in the .gtkc file and leave only the "include /home/daniel/.gtkrc.mine" line. And, of course, put something appropriate there. Maybe the schumacher font is the ugly one :)

Hope it helps

Visko

---

### Post by kerry_s on 2007-05-16
my gtkrc.mine for gtk1 fonts looks like this->

```
style "user-font"
{
  fontset="-dejavu-dejavu sans-medium-r-normal-*-*-120-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"

```

---

### Post by anti-dan on 2007-05-17
> **kerry_s said:**
> my gtkrc.mine for gtk1 fonts looks like this->

```
style "user-font"
{
  fontset="-dejavu-dejavu sans-medium-r-normal-*-*-120-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"

```
Alright! Now we're cooking with gas. Changing "font" (as gtk-theme-switch had insisted) to "fontset" worked a treat. My GTK 1 programmes look lovely now :)

Thanks for that.

---

