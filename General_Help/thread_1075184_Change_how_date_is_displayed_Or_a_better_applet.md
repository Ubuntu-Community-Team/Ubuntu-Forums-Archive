---
title: "Change how date is displayed? Or a better applet?"
date: 2009-02-20
forum: General Help
---

### Post by swoody on 2009-02-20
Well I Google'd quite a bit, but couldn't find anything useful so here goes. I've been trying to change the way the date is displayed on the default Gnome clock, but can't. I'd like to change it from it's current 'Fri Feb 20' to something like '2009-02-20' 

Is there any way to do this with this clock? I read some old post about going into gconf-editor and changing some settings, but things must have changed since that post, cause I couldn't find the settings for the panel clock. I'm supposed to be looking for:
/apps/panel/applets/applet_?/prefs/custom_format
but the 'applets' part isn't under 'panel'??

If there's no way to do this, is there a simple clock applet that I can add to gnome-panel to display the time/date the way I want it? I'd really rather not lose the neat Weather feature, and the International Info that this clock has, but I'd be open to it if I can get the date to display correctly.

Thanks in advance everybody! Any and all help is GREATLY appreciated.

---

### Post by dcstar on 2009-02-20
> **woody86 said:**
> Well I Google'd quite a bit, but couldn't find anything useful so here goes. I've been trying to change the way the date is displayed on the default Gnome clock, but can't. I'd like to change it from it's current 'Fri Feb 20' to something like '2009-02-20' 

Is there any way to do this with this clock? I read some old post about going into gconf-editor and changing some settings, but things must have changed since that post, cause I couldn't find the settings for the panel clock. I'm supposed to be looking for:
/apps/panel/applets/applet_?/prefs/custom_format
but the 'applets' part isn't under 'panel'??

If there's no way to do this, is there a simple clock applet that I can add to gnome-panel to display the time/date the way I want it? I'd really rather not lose the neat Weather feature, and the International Info that this clock has, but I'd be open to it if I can get the date to display correctly.

Thanks in advance everybody! Any and all help is GREATLY appreciated.

/apps/panel/applets/clock_screen0/prefs/format
/apps/panel/applets/clock_screen0/prefs/custom_format

[http://opengroup.org/onlinepubs/007908799/xsh/strftime.html](http://opengroup.org/onlinepubs/007908799/xsh/strftime.html)

---

### Post by swoody on 2009-02-20
Thanks for that link dcstar!

Well I just found out that running gconf-editor from the terminal makes some of the options not display, but running it from the menu seems to work fine :)

Now does anyone know how to change the date when you *mouse-over* the clock?

---

