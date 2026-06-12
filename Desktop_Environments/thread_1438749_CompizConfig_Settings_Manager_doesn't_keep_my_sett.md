---
title: "CompizConfig Settings Manager doesn't keep my setting!"
date: 2010-03-25
forum: Desktop Environments
---

### Post by Flywaver on 2010-03-25
Hi,
For some reasons CCSM doesn't retain my settings...e.g. I uncheck the following:
-Opacity, Brightness & Saturation
-Negative
-Widget Layer
-Animations
-Fading Windows
-Scale Addons
-Resize Info
-Place, Move, Scale Windows

If I close CCSM and reopen it, they are all checked ON!
Worst than that, if I uncheck animations it checks it back ON instantly! :(

I use Ubuntu Tweak but I make sure nothing conflicts with Compiz.
I use Normal for Visual Effects...but sometimes it unchecks it so there is no selection made!

I run Karmic 64-bit and my only issue is that when I minimize/maximize the windows there is a lag...even with the default human theme! :(

Any help would be appreciated!
Cheers!

---

### Post by 0x656b694d on 2010-03-25
check the permissions of your compizconfig folders may be?

These folders and files in them:
```
find ~ -type d -iname compiz* -exec ls -lad {} \;
```

(they are all drwx------ in my case)

---

### Post by Flywaver on 2010-03-26
They are all drwx except that after this I get:
find: `home/fly/.config/menus/applications-merged': Permission denied

---

