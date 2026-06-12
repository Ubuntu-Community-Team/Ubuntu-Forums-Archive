---
title: "Appearance Preferences 'frozen'"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by aweller on 2007-11-15
I have been messing around trying to get compiz to work, which I think is almost there (I have wobbly windows). I have a Dell Latitude D810 with a Mobility Radeon X300 card.

Ever since I have been playing, my Appearance Preferences (System > Preferences > Appearance) has been frozen. I can't seem to set anything (compiz, 'custom' compiz, etc). I have Ctrl + Alt + back space to reboot the X server.

Why has this happened? Is it possible to reset it?

Some outputs for you:

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)
```

I have also made composite extensions = "1" in my /etc/X11/xorg.conf:

```

Section "Extensions"
	Option		"Composite"	"1"
EndSection
```

```

$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```

I think that's it. I hope someone can help me...? Thanks.

---

### Post by nigel_salvador on 2008-03-18
I have the exact same problem. The Appearance Preferences window freezes such that I cannot tab over to the Visual Effects tab and change the settings. Have you found a solution to your problem as yet. If, so please pass on your knowledge thanks.

---

