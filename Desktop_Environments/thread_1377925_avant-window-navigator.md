---
title: "avant-window-navigator"
date: 2010-01-10
forum: Desktop Environments
---

### Post by kwyto on 2010-01-10
hi guys, i'm trying to install AWN. i have compiz, awn and awn manager installed. but when i go to accessories and try to run awn, nothing happens. any help is much appreciated.

---

### Post by howefield on 2010-01-10
Log out and back in. Might make the menu icon appear.

To open from terminal, (Applications > Accessories  >Terminal) type

```
avant-window-navigator &
```

---

### Post by kwyto on 2010-01-10
never mind drivers. i restarted the computer and now i can't change the appearance to normal or extra. the restricted driver i had installed it's not working. it was earlier. 

here is the output of the console after ```
 kwyto@ubuntu:~$ sudo compiz -fusion
[sudo] password for kwyto: 
Sorry, try again.
[sudo] password for kwyto: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1libGL error: XF86DRIAuthConnection failed
libGL error: reverting to (slow) indirect rendering
Comparing resolution (1600x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: xterm 
no xterm found, exiting

```

i'm running description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc

---

### Post by kwyto on 2010-01-11
ok. somehow its working now. the problem now it's trying to erase gnome-panel. I opened gconf-editor, found sessions and erase gnome-panel. after I restart the panel keeps showing up.

---

