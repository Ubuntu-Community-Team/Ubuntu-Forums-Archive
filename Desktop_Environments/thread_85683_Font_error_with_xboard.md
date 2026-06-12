---
title: "Font error with xboard"
date: 2005-11-03
forum: Desktop Environments
---

### Post by tigrez on 2005-11-03
It give me this error:

xboard: no fonts match pattern -*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*

why?

---

### Post by tigrez on 2005-12-30
Solved:
in /etc/xorg.conf there is the "files section"
the paths incorrectly link /usr/X11R6/bin/X11/font/...."
I think an flgrxconfig error...

---

### Post by RealMabu on 2008-01-22
I have the same error here. I have Ubuntu Gutsy Gibbon.
I have no /etc/xorg.conf but a /etc**/X11**/xorg.conf.
The "Files" section follows:
```

Section "Files"
        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

What's missing / wrong?

Thanks.
Mabu.

---

