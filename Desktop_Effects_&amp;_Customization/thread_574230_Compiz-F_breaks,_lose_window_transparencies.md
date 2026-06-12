---
title: "Compiz-F breaks, lose window transparencies"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by mikeserv on 2007-10-12
Apparently at random, Compiz-Fusion breaks - kinda.  Basically all that happens is that the transparencies that are set up in CF quit working, while all of the other effects keep on rolling.  It sometimes takes me a moment or two to notice that it's broken again.  When that happens there is an easy fix, I click on the taskbar icon (I'm using fusion-icon) and select "Reload Window Manager" and it all goes back to normal.  But it's still kind of annoying, especially if I have any tabbed window groupings setup at the time, because reloading undoes all of that.

Has anyone else experienced this problem and maybe isolated the issue?

-Mike

---

### Post by smartboyathome on 2007-10-12
Try running compiz fusion in a terminal (using compiz --replace), and then stop it when this happens again. Post the output here.

---

### Post by mikeserv on 2007-10-12
It does this right after starting it:
```
compiz --replace
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
```



And this when it breaks:


```
/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.
```



-Mike

Edit:  I put the code inside the [CODE] tags.

---

### Post by mikeserv on 2007-10-12
I enabled the text plugin, and that may have fixed it - I'm not yet sure.  At least I'm not getting any more, "Warn: No compatible text plugin loaded" messages.  But I'm still not sure what the handler deal is...

-Mike

Edit:  It didn't fix it.  The windows still break sometimes.

---

### Post by Forlong on 2007-10-13
Please post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by mikeserv on 2007-10-13
Output: 
```
ii  compiz-core                                0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20071006+3v1ubuntu0           Collection of Compiz Fusion plugins for Compiz - Extra
ii  compiz-fusion-plugins-main                 0.5.2~git20071007+3v1ubuntu0           Collection of Compiz Fusion plugins for Compiz - Main
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070921+3v1ubuntu0           Collection of UNOFFICIAL fusion plugins for Compiz
ii  compiz-fusion-plugins-unsupported          0.5.2~git20071006+3v1ubuntu0           Collection of plugins for Compiz - Unsupported
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk window dec
ii  compiz-plugins                             0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0          Plugin and configuration tool - Compiz Fusion Project
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu3           Settings library for plugins - Compiz Fusion Project
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration System
```

P.S.  What do you mean by "# button"?

---

### Post by Forlong on 2007-10-13
At least your packages are not mixed, so it must be an issue with them (they are bleeding edge, you know).

Consider switching to the stable packages by Amaranth: [http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)

(by "# button" I meant the one you use when making a post to get the CODE tags, but it seems like you found it :))

---

### Post by mikeserv on 2007-10-13
Maybe it's emerald?

```
dpkg -l | grep emerald
ii  emerald                                    0.5.2~git20071006+3v1ubuntu0           Decorator for Compiz and Beryl
ii  emerald-themes                             0.5.2~git20070812+3v1ubuntu0           Package of themes for Emerald
ii  libemeraldengine0                          0.5.2~git20071006+3v1ubuntu0           Decorator engines for Emerald
```

-Mike

P.S.  And I never found a "#" button, I just tried to quote you and found that you had embedded your code within " [ CODE ]  and  [ / CODE ] " tags (without the spaces, of course).

---

### Post by Forlong on 2007-10-13
> **mikeserv said:**
> Maybe it's emerald?
Maybe. I don't know, frankly, because I don't use those packages. I recommend using the backported ones from the guide linked above.


P.S. See attachment for the # button. :)

---

