---
title: "AWN can't use 3D or anything else except flat..."
date: 2010-05-16
forum: Desktop Environments
---

### Post by myromance123 on 2010-05-16
Hey there,
 
 Alright first things first.
My system specs are:
Processor - Core 2 Duo 2.0GHz
RAM - 4GB
Graphics card - Nvidia 9300M GS
Graphics Driver - 195.36.24 (proprietary)
OS - Ubuntu Studio 10.04 64-bit

I installed AWN via Ubuntu Software Center.
I currently can't get any cool features of AWN to work. Its stuck at flat and simple.

 When I do turn on the 3D style or icon effects or any other option besides the preset options, it gives me a weird looking (damaged) awn dock.
 All icons are still there, but dock background is weirded out.
It all returns to normal when I put the preferences back to the presets.

 Anyone else experiencing this? What could be causing this?
Any help is greatly appreciated.

PS: Could this have to do with why my Desktop Effects are not able to be activated as well? I can certainly play all my 3D games like Penumbra Overture and Lugaru HD. Blender works too.

---

### Post by willyclaes on 2010-05-17
I have eactly the same problem which I posted in another thread. I uninstalled AWN and I still can't enable desktop effects (without getting an error message, the video card isnt blacklisted, 9200M GS). Someone suggested to edit the xorg.conf file, without result, then adding it maybe is a conflict between metacity and compiz.

---

### Post by 3rdalbum on 2010-05-17
AWN does require desktop effects in order to get the full impact ("desktop effects" is provided by Compiz; it's a compositing window manager, and the compositing is what most docks rely on).

No idea why you can't get the effects though; try shutting down all programs, going to the terminal and running:

```
compiz --replace
```

See what error messages you get. Shut down the computer without closing the terminal; if you close the terminal you'll probably lose your window borders.

The other thing is, if Compiz won't work, you could always turn on Metacity's (the default window manager's) compositing. This is done by hitting Alt-F2 and typing:

```
gconf-editor
```

Under the 'apps' entry you can find Metacity, and then you can go from there and turn on compositing. This should make AWN work properly.

---

### Post by willyclaes on 2010-05-17
I entered "compiz --replace" in the terminal and had this error message:
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (core) - Error: Plugin 'text' not loaded.

compiz (shift) - Warn: No compatible text plugin loaded.

---

### Post by fabounet on 2010-05-17
seems your compositing is ok.
you may try GLX-Dock instead.
[http://www.glx-dock.org/ww_page.php?p=By%20distributions&lang=en]("http://www.glx-dock.org/ww_page.php?p=By%20distributions&lang=en")

---

### Post by willyclaes on 2010-05-18
I must say GLX-dock looks really nice.

It still would be nice if somebody knew how to fix the desktop effects issue with compiz.

---

