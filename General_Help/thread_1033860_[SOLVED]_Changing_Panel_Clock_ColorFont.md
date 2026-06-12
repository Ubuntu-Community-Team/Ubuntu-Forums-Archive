---
title: "[SOLVED] Changing Panel Clock Color/Font"
date: 2009-01-07
forum: General Help
---

### Post by pmshoop on 2009-01-07
For those like me with transparent panels (they're prettier)... Or for those that just want funky clocks... 

Ok all... With MUCH digging and MUCH playing I've figured out how to change the panel clock COLOR and FONT.  It's so simple ...

1) Open gconf-editor
2) Find in apps - panel - applets your clock applet (mine was called applet_2)
3) expand the clock applet to reveal the prefs page (click on the arrow beside the applet name on the left)
4) In the prefs page find the 'custom_format' line
5) double click to bring up the editing box. 
6) Add the below line of code
<span font = "Times New Roman Bold 12" color="green"> %a %b %d %I:%M </span> 
7) Find line 'format'
8) Change from 12-hour (or 24-hour) to custom (you got to type it in)
9) Close gconf-editor.  VIOLA!  

You MIGHT have to kill-all gnome-panel in a terminal.  I don't have to.

This beats the hell out of building a .gtkrc-2.0 file.  You can find a list of some font names here:
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

You can find more on the clock format (changing it to say full month name/day name/24-hour/12-hour/ etc...) here:
[http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html](http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html)
DON'T follow that pages formatting for color -- use the one I gave.

You can now tweak away.

:)

---

### Post by Sircoelho on 2009-03-08
Didnt work for me :( ](*,)

There is no clock_applet into "apps->panel->applets" the keys are default_setup (without any clock applet), general and global. 

The clock_applet and its "prefs - custom_format" is located at "schemas/applet/clock_applet"

When I try to edit the value I get this message:

**Currently pairs and schemas can't be edited. This will be changed in a later version.**

I'm using Ubuntu 8.10 updated!

---

### Post by Sircoelho on 2009-03-08
Nevermind.. I was using gconf in sudo mode :o

---

