---
title: "Tools That Helped me Get Compiz-Fusion Working on a Radeon Xpress 1100"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by aaaantoine on 2007-09-19
I'm posting this for a couple of reasons.

1. In Feisty, it's rather difficult to get Compiz working on a Radeon Xpress 1100.  This thread is to (partially) help out others trying to get it to work.
2. I need a place to keep my links in case I do a clean install.

Assuming you have ATI's FGLRX drivers installed, assuming you have an XGL session configured, and assuming you have compiz-fusion installed, the following links should help you get the rest of the way there:

If you're getting **GLX_EXT_texture_from_pixmap is missing**, go here:
[http://blog.micampe.it/articles/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap](http://blog.micampe.it/articles/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap)
The location of your mesa lib may vary.  Mine successfully launched with this command:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace gconf
```

If you're getting **No GLXFBConfig for default depth, this isn't going to work.** (such a pessimistic error message, by the way), go here:
[http://forum.compiz-fusion.org/showthread.php?t=3350](http://forum.compiz-fusion.org/showthread.php?t=3350)

If you have no window borders, try **emerald --replace** in a terminal.

Does Emerald give you trouble?  Try the [Gnome Compiz Manager](http://compiz.org/Gnome_Compiz_Manager) instead.

If compiz crashes and you're stuck with immovable windows, type this:
```
metacity --replace
```

To load your gnome theme settings in your XGL session:
1. Go to System -> Preferences -> Sessions
2. Add a new startup program that runs the command **gnome-settings-daemon**

For other installation notes, search this forum for answers.

A note for XGL: Shift + Backspace kills the session.  Something to keep in mind while you're typing up your thesis (on an unstable system!? What's wrong with you?)

Cheers!

---

