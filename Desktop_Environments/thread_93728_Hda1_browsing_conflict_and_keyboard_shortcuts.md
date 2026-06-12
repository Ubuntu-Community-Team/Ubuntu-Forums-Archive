---
title: "Hda1 browsing conflict and keyboard shortcuts"
date: 2005-11-22
forum: Desktop Environments
---

### Post by kocas on 2005-11-22
i have both winxp and ubuntu. I activated the root account and i am able to browse /media/hda1  (which is a  NTFS system and a primary partition) through the terminal. however, the shortcut at my desktop to hda1 keeps saying that i do not have the permissions to see the contents of hda1. when i look at the properties of hda1, i see that the permissions are all disabled. It wants a "owner" status and says that i am not the owner. it is pretty hard to read from hda1 through terminal every time, and it is idiotic to read the "owner's" drive in some other way :)
maybe it is too simple..:D
please help..



ps: some kboard shortcuts do not work also. my keyboard is turkishQ and when i try to select the proper layout, there pops a bunch of errors like:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
____________________________________________

"-root" is mentioned above, which i do not feel very comfortable with :D

thanks..

---

### Post by aysiu on 2005-11-24
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs) should solve your first problem. I don't know about the keyboard shortcuts.

---

### Post by kocas on 2005-11-24
i was able to solve my  ntfs problem, but problem was a little different. i was not able to use your suggestion because in the terminal, it was not possible to know sudo pass. first created a root login, and then was able to perform the operations. 
 But thanks anyway! i did not know this way of solving that problem. 

by the way i think keyboard layout problem is a bug that needs to be ironed out soon. i heard there were problems with other languages also.

---

### Post by aysiu on 2005-11-24
The sudo password is the same as the password of the first user created during installation. For more on this, go here:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

