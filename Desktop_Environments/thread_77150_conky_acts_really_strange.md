---
title: "conky acts really strange"
date: 2005-10-16
forum: Desktop Environments
---

### Post by anatole on 2005-10-16
hi,
i just installed breezy, and installed conky also, it worked fine for me on hoary.
now it acts really strange... i think i cannot describe so i'll post a screenshot, and also my conkyrc. (note: running conky in a window or as a part of a desktop is irrelevant for the matter, which happens both ways)

as you can see on the screenshot its quite strange, and also its blinking like hell (even when running it in a separate window..)
you see my error messages too, i don't know how to fix it... any help would be welcome :)

---

### Post by Stormy Eyes on 2005-10-16
[QUOTE=anatole]hi,
i just installed breezy, and installed conky also, it worked fine for me on hoary.[/QUOTE]

The conky package in Breezy universe was built without Xft and double buffer support. Use the deb package from [SourceForge](http://sourceforge.net/project/showfiles.php?group_id=143975&package_id=158249&release_id=353061) that matches your CPU type (i386, PPC, AMD64). I already filed a bug concerning this, and it's an upstream issue; the Debian Sid maintainer has to rebuild the package.

I use the Deb from SourceForge myself; it works on both Hoary and Breezy.

---

### Post by anatole on 2005-10-16
[QUOTE=Stormy Eyes]The conky package in Breezy universe was built without Xft and double buffer support. Use the deb package from [SourceForge](http://sourceforge.net/project/showfiles.php?group_id=143975&package_id=158249&release_id=353061) that matches your CPU type (i386, PPC, AMD64). I already filed a bug concerning this, and it's an upstream issue; the Debian Sid maintainer has to rebuild the package.

I use the Deb from SourceForge myself; it works on both Hoary and Breezy.[/QUOTE]

i tried that too. only improvement that the letters are bigger, it looks like the one i used on hoary, but still, it blinks every second and its fulfilled with multiplicated unnecessary lines like "playing" and the ones showing numbers... i tried it with disabling the xmms plugins but the problems remained... it seems to be a conky issue...

---

