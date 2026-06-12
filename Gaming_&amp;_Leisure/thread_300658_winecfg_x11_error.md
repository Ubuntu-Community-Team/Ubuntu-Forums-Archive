---
title: "winecfg x11 error"
date: 2006-11-16
forum: Gaming &amp; Leisure
---

### Post by ninjameb on 2006-11-16
I used the repo from winehq to install wine 9.25, but when i try to run winecfg, I get an error:

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!



Sorry if this is a stupid question....I'm rather new to ubuntu, and havent quite figured everything out yet. Is there something obvious i'm doing wrong?


thanks.


edit: i get the same error with $wine notepad.exe

x11 just doesn't want to open a window?

---

### Post by Xenix on 2006-11-21
> **ninjameb said:**
> I used the repo from winehq to install wine 9.25, but when i try to run winecfg, I get an error:

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!


I also get this error when trying to run winecfg once compiled from source.  I have to compile from source, in order to apply the Continuum / Subspace patch, as the pre-compiled version doesn't give many any sound and sometimes doesn't work.  I am using Wine 0.9.25

Any ideas?

Thanks in advance.

---

