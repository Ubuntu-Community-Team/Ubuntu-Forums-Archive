---
title: "No unity after installing TLP"
date: 2013-07-20
forum: Desktop Environments
---

### Post by Luxor125 on 2013-07-20
Hello,

I'm running Ubuntu 13.04 on my laptop and everything was fine until yesterday when I installed TLP to try getting more battery life.
After installing TLP and rebooting, I can't use unity anymore: no launcher, no dash, etc.

If I run the command "unity" from terminal I get:

```

unity-panel-service: no process found
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.


compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.


Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
...
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

```

and the keyboard stops working so I have to power it down and boot up again.

I tried resetting unity to default with 
```

dconf reset -f /org/compiz

```
and also reinstalling it, reinstalling intel video card drivers, but nothing worked so far.

Thanks for the help.

---

