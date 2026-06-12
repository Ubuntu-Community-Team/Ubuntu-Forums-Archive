---
title: "Kubuntu 9.10 fails to boot usplash? help!?"
date: 2009-12-15
forum: Desktop Environments
---

### Post by 11zac11 on 2009-12-15
Ok i had Kubuntu 9.10 64bit running fine for a good few weeks on my desktop until a few days ago usplash stopped working. 
Now what happens when i turn my computer on once kubuntu is selected from the GRUB menu, the first loading bar with the kubuntu logo loads fine then the screen flickers and i get dumped to tty2, If i look at tty1 i find this message 'usplash: settings mode 1152x864 failed, usplash: Using mode 1024x768'.
I can log into tty2 fine and it brings up the command line and lets me run commands etc. however i would like to get back to my desktop!
Is there anyone that can help me?
In case you need to know my graphics card is the geforce 9800GT 1GB and i have a dual 19inch monitor set up with this both running at 1400x900. If you need to know anything else please feel free to ask!

---

### Post by pixel :-) on 2009-12-15
hopefully to get you back at your desktop, deactivate the splash screen

1.chose the recovery mode at boot, it will drop in a menu, just choose to continue normal boot

2. At grub, chose to edit the start up options, remove(for only this boot up) the splash option, forgot the exact name, it should be obvious.

---

### Post by 11zac11 on 2009-12-16
Thank you for the reply however after removing the splash in the grub boot it still does the same thing, anymore ideas ?

---

