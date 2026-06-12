---
title: "[jaunty] Visual Effects reset to &quot;none&quot; after reset/logout"
date: 2009-05-22
forum: General Help
---

### Post by jetersauce on 2009-05-22
Suddenly today whenever I reset or logout my visual effects get set back to none.  I've found a few threads with people having the same problem but none of the solutions have worked.

_Solutions I've tried_

1) I used the compiz-check found in this thread: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
and got the following output
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 9800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```
2) I tried installing fusion-icon and adding it to startup applications.  This caused my machine to lag heavily.

3) I tried installing simple ccsm and setting the effect to "custom".  This did nothing, it reset to "none" again.

Any help with this would be greatly appreciated :D I know there are some others out there with this problem that would appreciate it as well.

---

### Post by Kidwell on 2009-07-08
well, i can't offer a perfect answer, but as a work around i've placed a Compiz startup in the startup sessions, with compiz --replace as the command, it works, but i'm still puzzled why this happens, my wifes login does not suffer from the same effect, so it must be in my config files, i've tried purging and reinstalling, but to no avail.  I also lost all the extra animations, even though i know they are installed.  Using Jaunty

---

### Post by CatKiller on 2009-07-08
The documentation says that the key is deprecated, but you might want try opening gconf-editor and setting the /desktop/gnome/applications/window_manager/current and /desktop/gnome/applications/window_manager/default keys to /usr/bin/compiz.

---

### Post by MathUHenry on 2009-12-30
Thank you Kidwell, that fixed my Karmic.

---

