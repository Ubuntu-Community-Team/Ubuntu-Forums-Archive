---
title: "How / where is Xft.lcdfilter enabled?"
date: 2011-06-21
forum: Desktop Environments
---

### Post by Danny Darko on 2011-06-21
Hi,

This has been puzzling me for some time; I'd like to know where the Xft.lcdfilter parameter is set by default. I thought it was set by /etc/fonts/conf.d/11-lcd-filter-lcddefault.conf, but if I remove this file and restart X it is still enabled:

```
$ xrdb -query
Xft.dpi:    96
Xft.antialias:    1
Xft.hinting:    1
Xft.hintstyle:    hintslight
Xft.rgba:    rgb
Xft.lcdfilter:    lcddefault
```It doesn't seem to appear in the global or user-specific Xresources files. The GNOME "Appearance" applet doesn't have an option for lcdfilter. Might it be hard-coded into the library?

Any help would be appreciated. I'd like the option to change or disable lcdfilter at its earliest setting.

Thanks!

---

