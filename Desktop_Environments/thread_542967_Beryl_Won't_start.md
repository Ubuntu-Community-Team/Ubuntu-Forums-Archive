---
title: "Beryl Won't start"
date: 2007-09-04
forum: Desktop Environments
---

### Post by happysmileman on 2007-09-04
I run Kubuntu 7.04 and had Beryl for a few days working fine, now all of a sudden, after switching theme on KDE it won't start. I know this is probably the theme's fault, but I'd like to keep it.

So does anyone know what this means:

```
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setFont: Will be reset by begin()
QPainter::end: Missing begin() or begin() failed
The program 'beryl-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 456 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

It appears that there's an integer out of range, anyone know any way I could fix this without having to remove theme (if that's the only way I'll have to think long and hard about whether to have sexy beryl without this theme or sexy theme without beryl so hopefully I won't have to go through that

---

### Post by Happy_Man on 2007-09-04
Hmm.... does this theme have an icon for beryl-manager? If so, try deleting those icons, and seeing if that works.

---

### Post by happysmileman on 2007-09-04
> **Happy_Man said:**
> Hmm.... does this theme have an icon for beryl-manager? If so, try deleting those icons, and seeing if that works.

You mean a menu icon? In the menu there's no icon for Beryl-Manager, is that a problem?

---

### Post by Happy_Man on 2007-09-04
No, I mean in ~/.kde/share/icons, there should be a folder that contains all the icons. See if there is an icon for beryl-manager, and delete it.

---

### Post by happysmileman on 2007-09-04
> **Happy_Man said:**
> No, I mean in ~/.kde/share/icons, there should be a folder that contains all the icons. See if there is an icon for beryl-manager, and delete it.

There isn't even a "~/.kde/share/icons"

```
paul@Computer:~$ ls -a ~/.kde/share/
.  ..  applnk  apps  config  locale  mimelnk  services  servicetypes
```

---

### Post by happysmileman on 2007-09-04
Solved it with only small change to theme, twas the Kore for Domino style that caused it, colours and rest of theme work, and my fix was to just use the "Plastik" style, but still use the Domino (with Kore mod) colour settings and the rest of Kore theme

---

