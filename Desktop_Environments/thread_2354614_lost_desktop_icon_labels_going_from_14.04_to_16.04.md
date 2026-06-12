---
title: "lost desktop icon labels going from 14.04 to 16.04"
date: 2017-03-04
forum: Desktop Environments
---

### Post by eugener on 2017-03-04
When I moved my system from a 14.04 box to a new 16.04 laptop, the old icons showed up as very small and without labels.  I can increase their size, but do not seem to be able to label them.   Any suggestions welcome.

---

### Post by #&amp;thj^% on 2017-03-04
Well with no clear direction or error's showing...have you yet tried this:
 Lets start by makeing a backup and keep the configuration ( or you may just need rename .config ).
```
mv  ~/.config Documents/Backupcfg
```
This makes a backup of the .config folder and moves it to your Documents Folder.
It will be named as Backupcfg as a folder. (Just encase we need it later.)
Next try this in the terminal:
```
rm -rf  ~/.config
```
Now Reboot.
Any improvement now?

---

