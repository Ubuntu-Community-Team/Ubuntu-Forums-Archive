---
title: "Desktop Effects not working correctly"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by lpsavoie on 2007-04-22
Hi,

I'm trying to run Compiz on my Feisty Fawn box. Annoyingly enough, though, window decorations never appear : it is therefore unusable !

I updated from Edgy and compiz never worked correctly, although Beryl did (I'd rather use compiz though).

Here's my box's configuration :
```
Motherboard	Asus A7V8X-X
CPU	AMD Athlon(TM) XP 2500+
System Memory	512MB
VGA compatible controller	NV18 [GeForce4 MX 440 AGP 8x]
ATA Disk	ST3120814A	Seagate
```

And here's the output given by desktop-effects :
```
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory
/usr/bin/compiz.real: pixmap 0x4c00143 can't be bound to texture
[...]
/usr/bin/compiz.real: Couldn't bind redirected window 0xc00bde to texture
/usr/bin/compiz.real: pixmap 0x4c00145 can't be bound to texture
/usr/bin/compiz.real: Couldn't bind redirected window 0xc00b03 to texture
Window manager warning: Locale not understood by C library, internationalization will not work
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "unmaximize"
```

---

### Post by orb9220 on 2007-04-22
Post your xorg.conf here.
Also check it and make sure depth is 24 not 32

---

### Post by flyboy284 on 2007-04-24
Please post your xorg.conf. My box is similar and i'd like to see your xorg file to help troubleshoot my system.
thanks

---

