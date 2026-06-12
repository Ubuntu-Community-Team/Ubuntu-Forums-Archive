---
title: "feisty text bug"
date: 2007-04-21
forum: Desktop Environments
---

### Post by jeamer on 2007-04-21
Upgraded to 7.0.4 and was fine until restart, now any desktop-related text (outside of programs) is just boxes... anyone know how to change the font through the terminal?? Thanks.

---

### Post by zerwas on 2007-04-21
the command for the dialog to change the font is 

```
gnome-font-properties
```

Good luck,
zerwas

---

### Post by jeamer on 2007-04-21
Thanks... unfortunately that opens the window for it, of which I can't read! A clue may be that on executing that command I got about 30 of these error messages in the terminal:

(gnome-font-properties:4969): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

Maybe Cairo is the block font... I don't know. I even tried messing with random things in the font window... to no avail. Maybe not a font problem?

---

### Post by zerwas on 2007-04-22
Sorry that that didn't solve your problem.

One question: Are you using a 64bit system?

And have you installed all libpango* packages?

---

### Post by jeamer on 2007-04-22
That may have been it... did a clean install last night and everything seems to be OK. Thanks for your help!

---

### Post by Bertie on 2007-05-27
Help! I am having the same problem! I had happily installed dapper then thought I'd be brave and go KDE so followed the instructions on 
[http://zerlinna.blogweb.de/archives/95-Install-Kubuntu-Breezy-Step-2-Upgrade-to-Kubuntu.html](http://zerlinna.blogweb.de/archives/95-Install-Kubuntu-Breezy-Step-2-Upgrade-to-Kubuntu.html) . 

Now all I see is my normal ubuntu desktop, but all the characters are rectangles :-(

Terminal, firefox, etc., work fine, but everything else is rectangles. The only clue I got was when I tried doing a gedit and got the same error messages:

[COLOR="#0000ff"][B]sys: 1: PangoWarning: No builtin or dynamically loaded modules were found. This probably means that there was an error in the creation of: '/etc/pango/pango.modules'. You should create this file by running pango-querymodules.
sys: 1: PangoWarning: pango_shape called with bad font, expect ugly output
sys: 1: PangoWarning: pango_font_get_glyph_extents called with bad font, expect ugly output
sys: 1: PangoWarning: pango_font_get_font_map called with bad font, expect ugly output
sys: 1: PangoWarning: pango_cairo_font_map_get_renderer: assertion 'PANGOIS-CAIRO-FONT-MAP (fontmap) failed
sys: 1: PangoWarning: _pango_cairo_font_install called with bad font, expect ugly output
sys: 1: PangoWarning: pango_font_get_metrics called with bad font, expect ugly output.[/B][/COLOR]

I guess my question is a cry for **[COLOR="Red"]HELP[/COLOR]****... what shall I do to get back to drake (or anything that works!)?**

---

