---
title: "Compiz/desktop effects assistance"
date: 2008-12-29
forum: General Help
---

### Post by Lief on 2008-12-29
Running an inspiron 1420 fresh install of 8.10, attempting to enable desktop effects to no avail, not sure if its the drivers or what, ran [http://ubuntuforums.org/showthread.php?t=799070&highlight=Visual+effects+enable](http://ubuntuforums.org/showthread.php?t=799070&highlight=Visual+effects+enable) to see what the exact problem was, came out with  Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

anyone able to help? (brand new to ubuntu but I'm really trying to figure this out)

Poked around for some other help on the forum but was having a hard time finding exactly what I'm looking for, thats how I ended up finding the script.

---

### Post by Lief on 2008-12-29
tagging on to this, I have the exact same problem.

Except that my problem is in 8.10

---

### Post by Lief on 2008-12-29
Hey overdrank I did the compiz check however I couldnt really understand what it was telling me was failing, I posted them a couple hours ago but no response yet, any chance you could take a look? 
[http://ubuntuforums.org/showthread.php?t=1025089](http://ubuntuforums.org/showthread.php?t=1025089)

---

### Post by overdrank on 2008-12-29
> **Lief said:**
> Hey overdrank I did the compiz check however I couldnt really understand what it was telling me was failing, I posted them a couple hours ago but no response yet, any chance you could take a look? 
[http://ubuntuforums.org/showthread.php?t=1025089](http://ubuntuforums.org/showthread.php?t=1025089)

Hi and I have seen issues with intel graphics on intrepid but do not have a solution.

---

### Post by Lief on 2008-12-29
oh darn :( it seems to be a driver error since I know for a fact that my model of laptop (same graphics card) can come with ubuntu pre installed... and when you do that it seems to work fine, which files it down to a driver error... the big problem is that the driver app isnt finding the driver necessary and many newbs (including myself) lack the skills to figure out how to get the driver we need, even if its found. (sorry to hijack thread)

---

### Post by overdrank on 2008-12-29
> **Lief said:**
>  (sorry to hijack thread)

Moved to your thread. Did you try using Hardy 8.04 as it should work well with the intel graphics.

---

### Post by Lief on 2008-12-29
Yeah I tried hardy a while ago, I'm going to see if I can find a way to get the driver I need, I think I know what I need, but I dont really understand how to get something from a git repository...  [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) the first one should be what I need but I really dont understand git commands.

---

### Post by ubuntu-freak on 2008-12-30
From what I've read about the bug, you're better off using Hardy and then hopefully the bug will be fixed in time for Jaunty. Desktop effects worked fine for me in Hardy with an X3100 (GM965) graphics chipset. Plus you get the prettier Hardy wallpaper... ;)

P.S. You can read about the bug [here](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094).

---

