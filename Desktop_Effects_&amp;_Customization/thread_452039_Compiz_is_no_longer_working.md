---
title: "Compiz is no longer working"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by hughgurt on 2007-05-22
I installed the Compiz update from Update Manger this morning.  All was well till I rebooted and I noticed it started using the Metacity theme.  I went into GL Desktop to enable GL Desktop but it defaulted back to Metacity; clicking Enable Desktop Effects in Desktop Effects would do the same.  Going into console and typing compiz would result in this:

hugh@boon:~$ compiz
GLX_EXT_texture_from_pixmap is not available with direct rendering.
GLX_EXT_texture_from_pixmap is available with indirect rendering.
/usr/bin/compiz.real: Unknown option '--no-fbo'
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

And typing in compiz --replace gconf: 

hugh@boon:~$ compiz --replace gconf
GLX_EXT_texture_from_pixmap is not available with direct rendering.
GLX_EXT_texture_from_pixmap is available with indirect rendering.
/usr/bin/compiz.real: Unknown option '--no-fbo'
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any thoughts on what the problem is and how I may rectify it? Thanks!

---

### Post by ronocdh on 2007-05-23
I believe that the current versions of Beryl do not support most ATI cards, and so an older version of Beryl must be used in conjunction with an XGL session in order to have the effects work. If the user updates Beryl, the functionality breaks. Perhaps there is a similar issue with Compiz?

---

### Post by hughgurt on 2007-05-23
ronocdh, thanks for your reply.  Following your suggestion of downgrading, I went into Synaptic and forced all the installed Compiz components to downgrade from 0.5 back to 0.3.6 and, whala, it's working again!

---

### Post by kustavo on 2007-07-29
**[SIZE="3"]undefined symbol: decor_apply_gravity[/SIZE]** 

[http://codigosecreto.blogspot.com/2007/07/soluo-erro-undefined.html](http://codigosecreto.blogspot.com/2007/07/soluo-erro-undefined.html)
[B]Translation:
Update libdecoration0 for version 1:0.5xxx[/B]

---

