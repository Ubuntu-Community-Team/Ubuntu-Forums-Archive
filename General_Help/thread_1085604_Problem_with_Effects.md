---
title: "Problem with Effects"
date: 2009-03-03
forum: General Help
---

### Post by Qwertylol on 2009-03-03
I have installed a package that gives me options to add/change windows effects, I can't remember what it's called but it ends in ix or something (can't check now as I need to go out but can when I come back in 2ish hours).

Using this, I enabled the window blur effect- but my graphics card isn't good enough to support this so now all I see is a black screen with the odd red border around windows.

I have tried using failsafe gnome and terminal to uninstall this but it hasn't worked.

I have another ubuntu login with no permissions whatsoever.

Please help!

---

### Post by Qwertylol on 2009-03-03
It's called compiz

---

### Post by philinux on 2009-03-03
If you can get into a terminal then use.

```
metacity --replace
```

---

### Post by Qwertylol on 2009-03-03
[COLOR="LightBlue"][B]I just uninstalled compiz-* then, to get back the windows I edited  /etc/X11/xorg.conf and added 

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True" 

to device. 

Now when I load ubuntu I get: "No resume image, doing normal boot..." and it prompts me to log in on a black screen, which is basically a terminal - no login screen :(

Now what??[/B][/COLOR]

---

