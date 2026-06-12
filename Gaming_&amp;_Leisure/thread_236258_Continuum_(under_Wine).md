---
title: "Continuum (under Wine)"
date: 2006-08-14
forum: Gaming &amp; Leisure
---

### Post by Prae on 2006-08-14
As far as explaining what Continuum is, in depth, I would visit [http://getcontinuum.com/](http://getcontinuum.com/) - but simply, it's a 2D space shooter MMOG.

For installation - [http://wine.getcontinuum.com/](http://wine.getcontinuum.com/) (Or for Windows, simply getcontinuum.com)


-

I hope someone here enjoys the game as much as I do =).  I'm going on my fifth year of playing, and the addiction has never been more severe ;).  I'm in SSCB Redstar (one of Continuum's zones)!  Give me a holler!

---

### Post by eqisow on 2006-08-14
```
wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: symbol wine_casemap_lower, version WINE_1.0 not defined in file libwine.so.1 with link time reference
```

Initially it said it failed to find /usr/local/lib/wine/ntdll.dll.so so I created a symbolic link from /usr/lib/wine/ntdll.dll.so and then I got the error above.

Edit: I am currently trying compiling Wine myself with their patch. If this works I will create a new Wiki page with the patched version. Hopefully the patch won't have any advserse effects on WoW and I will be able to maintain one patcehd Wine version for both games.

---

### Post by eqisow on 2006-08-14
Well I finished compiling and I can get Continuum to install and run fine. However, after I log into a server my ship appears and dissapears randomly and other ships are completely invisible. In Windows mode, this problem goes away, but the graphics become very distorted. They are turned at a 45 degree angle and the colors are very messed up, almost as if you're watching a 3D video without the glasses.

I messed with the settings a bit, but was unable to improve upon my results.

Edit: [http://bugs.winehq.org/attachment.cgi?id=3081&action=view](http://bugs.winehq.org/attachment.cgi?id=3081&action=view)

---

### Post by eqisow on 2006-08-14
OK, I got Continuum working well under Wine with the following settings:

Windows version: XP
Emulate a Vertiual Desktop: On
DirectSound hardware acceleration: emulation

The only problem now is that the virtual desktop is a universal settings and can't be changed on an application by application basis. Does this mean I'm stuck opening winecfg to turn it off whenever I want to play WoW?

---

### Post by Prae on 2006-08-14
Looks like it, sorry, I didn't develop the binary.  I'll post this thread on ssforum.net, which might have a little more information you want (Look in General Discussion -> Thread entitled "wine.getcontinuum.com").

---

