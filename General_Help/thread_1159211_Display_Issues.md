---
title: "Display Issues"
date: 2009-05-14
forum: General Help
---

### Post by skvarcej on 2009-05-14
Hey guys,
I boot up my comp, and everythings fine.  The splash screen loads up, i type in my info, and then my monitor goes blank, telling me "Mode Not Supported."  I know what caused this, I booted up this morning and my display was out of wack, so I tried to fix it, and when i set it to a higher resolution, the screen blanked and never reset automatically.  Any help would be greatly appreciated, I feel like I've scoured the internet for information.

---

### Post by overdrank on 2009-05-14
> **skvarcej said:**
> Hey guys,
I boot up my comp, and everythings fine.  The splash screen loads up, i type in my info, and then my monitor goes blank, telling me "Mode Not Supported."  I know what caused this, I booted up this morning and my display was out of wack, so I tried to fix it, and when i set it to a higher resolution, the screen blanked and never reset automatically.  Any help would be greatly appreciated, I feel like I've scoured the internet for information.

Hi and welcome, you may try and boot into recovery mode which is usually the second choice from the grub when booting. You should be given 4 option and one is xfix. After running xfix to correct the graphical issue you should be given the 4 options again where you can choose to boot normally.

---

### Post by skvarcej on 2009-05-14
Thanks, and thanks for the quick reply.  I did try xfix before, and essentially it tells me its going to overwrite any user settings, then brings me back to the menu.  After booting normally the issue still persists.

---

### Post by overdrank on 2009-05-14
Ok what is the model of the graphics card and version of Ubuntu?
Can you reach the command prompt by using the ctrl. alt, F1 keys is yes then you may try the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by skvarcej on 2009-05-14
I have an nvidia, and i'm running 9.04 with ubuntustudio upgrades. I can get into the prompt so i'll give it a shot.  It also might be worth noting that when I use a different screen the problem doesn't exist.

---

### Post by skvarcej on 2009-05-14
Also, that didn't work either.  I'm starting to get really curious about what I did to have this happen ha.  Obviously i'm pretty new to linux, I just starting migrating from OS X.

---

