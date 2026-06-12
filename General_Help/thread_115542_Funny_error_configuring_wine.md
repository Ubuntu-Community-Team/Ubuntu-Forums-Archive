---
title: "Funny error configuring wine"
date: 2006-01-10
forum: General Help
---

### Post by Damburger on 2006-01-10
I get the following when I run winecfg (or any application under wine):

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

I can't find anything about this in the wine documentation, so I thought it might be something specific to ubuntu.

Can anyone help?

---

### Post by dcstar on 2006-01-10
[QUOTE=Damburger]I get the following when I run winecfg (or any application under wine):

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

I can't find anything about this in the wine documentation, so I thought it might be something specific to ubuntu.

Can anyone help?[/QUOTE]
Probably a corrupted wine installation, rename you (hidden) .wine directory and try again (you will have to re-install all your Windows apps).

---

### Post by Damburger on 2006-01-10
I have tried that, and managed to reproduce the exact same error, so its something systematic not random.

Actually, this may be the wrong forum for this thread, seeing as I have an amd64 version of Ubuntu. That might have something to do with my wine problems :(

EDIT: Found the same error in this thread: [http://www.ubuntuforums.org/showthread.php?t=96620&page=2](http://www.ubuntuforums.org/showthread.php?t=96620&page=2)
It is a 64-bit problem

---

