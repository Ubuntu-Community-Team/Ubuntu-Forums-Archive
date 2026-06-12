---
title: "Font from package &quot;cmatrix-xfont&quot; not installed in correct location."
date: 2006-07-05
forum: Desktop Environments
---

### Post by gossea on 2006-07-05
Recently installed packages cmatrix and cmatrix-xfont.  The font was installed to the incorrect location (likely a debian package issue):

```

$ cat /var/lib/dpkg/info/cmatrix-xfont.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/cmatrix-xfont
/usr/share/doc/cmatrix-xfont/copyright
/usr/share/doc/cmatrix-xfont/changelog.gz
/usr/share/doc/cmatrix-xfont/changelog.Debian.gz
/usr/X11R6
/usr/X11R6/lib
/usr/X11R6/lib/X11
/usr/X11R6/lib/X11/fonts
/usr/X11R6/lib/X11/fonts/misc
/usr/X11R6/lib/X11/fonts/misc/mtx.pcf.gz

```

I had to manually add /usr/X11R6/lib/X11/fonts/misc to /etc/X11/xorg.conf in order to get xlsfonts to list "mtx" (to get X to load fonts in the same patch). 

Now, `xterm -fn mtx` works properly, but mtx is still not visible in the font chosers in xfce4 - and therefore I cannot pick mtx as the font for "Terminal".  Attempting to edit terminalrc and change the font manually to mtx causes Terminal to load it's default font.

Does it really make sense to be able to pick all kinds of variable-width and true-type fonts for a terminal emulator, but not even be able to pick simple fixed-width ones?

This is a long time pet peeve of mine.

-- 
Alex

---

