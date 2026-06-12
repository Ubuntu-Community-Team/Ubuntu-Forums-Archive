---
title: "startx problem"
date: 2006-06-22
forum: Desktop Environments
---

### Post by tchock on 2006-06-22
After a reboot, if I type startx, X will crash the first time. If I type it again, it will start. Here is a diff between my Xorg.0.log (worked) and my Xorg.0.log.old (didn't):

```
< (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 23:06:57 2006
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 23:06:41 2006
504c504,506
< drmOpenDevice: open result is 6, (OK)
---
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: Open failed
2047,2049c2049,2051
< (II) fglrx(0): [drm] added 8192 byte SAREA at 0xe000
< (II) fglrx(0): [drm] mapped SAREA 0xe000 to 0xb71d3000
< (II) fglrx(0): [drm] framebuffer handle = 0xf000
---
> (II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
> (II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb729d000
> (II) fglrx(0): [drm] framebuffer handle = 0x3000
2063c2065
< (II) fglrx(0): [drm] register handle = 0x00010000
---
> (II) fglrx(0): [drm] register handle = 0x00004000
2073c2075
< (II) fglrx(0): [drm] texture shared area handle = 0x00014000
---
> (II) fglrx(0): [drm] texture shared area handle = 0x00008000
2143a2146,2148
> (II) fglrx(0): [drm] removed 1 reserved context for kernel
> (II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb729d000
> FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.
```

Does any of that seem off to anyone?

---

### Post by scottylans on 2006-06-22
[QUOTE=tchock]After a reboot, if I type startx, X will crash the first time. If I type it again, it will start. Here is a diff between my Xorg.0.log (worked) and my Xorg.0.log.old (didn't):

```
< (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 23:06:57 2006
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 23:06:41 2006
504c504,506
< drmOpenDevice: open result is 6, (OK)
---
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: Open failed
2047,2049c2049,2051
< (II) fglrx(0): [drm] added 8192 byte SAREA at 0xe000
< (II) fglrx(0): [drm] mapped SAREA 0xe000 to 0xb71d3000
< (II) fglrx(0): [drm] framebuffer handle = 0xf000
---
> (II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
> (II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb729d000
> (II) fglrx(0): [drm] framebuffer handle = 0x3000
2063c2065
< (II) fglrx(0): [drm] register handle = 0x00010000
---
> (II) fglrx(0): [drm] register handle = 0x00004000
2073c2075
< (II) fglrx(0): [drm] texture shared area handle = 0x00014000
---
> (II) fglrx(0): [drm] texture shared area handle = 0x00008000
2143a2146,2148
> (II) fglrx(0): [drm] removed 1 reserved context for kernel
> (II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb729d000
> FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.
```

Does any of that seem off to anyone?[/QUOTE]



I beleive I'm in a similar boat, since the most recent updates yesterday or the day before or something >: (

---

### Post by tchock on 2006-06-22
Yes this happened to me after updating as well; it's just good to know I'm not the only one. Also a sign that maybe it will be fixed and I can stop trying to find ways to fix it myself.

---

### Post by scottylans on 2006-06-23
[QUOTE=tchock]Yes this happened to me after updating as well; it's just good to know I'm not the only one. Also a sign that maybe it will be fixed and I can stop trying to find ways to fix it myself.[/QUOTE]


Anyone got a solution, I re-installed but now I'm back to square one!
[http://ubuntuforums.org/showthread.php?p=1171394#post1171394](http://ubuntuforums.org/showthread.php?p=1171394#post1171394)


Is it safe for me to re-install nvid drivers?
1600x1200 is killing me.

---

### Post by scottylans on 2006-06-24
[QUOTE=scottylans]Anyone got a solution, I re-installed but now I'm back to square one!
[http://ubuntuforums.org/showthread.php?p=1171394#post1171394](http://ubuntuforums.org/showthread.php?p=1171394#post1171394)


Is it safe for me to re-install nvid drivers?
1600x1200 is killing me.[/QUOTE]



Anyone plz?

---

