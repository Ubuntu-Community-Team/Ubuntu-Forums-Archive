---
title: "xfce desktop replaced by launching nautilus"
date: 2005-08-10
forum: Desktop Environments
---

### Post by g7yh7uj8k on 2005-08-10
I am using xfce. I launched nautilus and the background changed and the desktop icons from gnome showed up. I looked around and found out that I should have use the  --no-desktop flag and this would not have happened. Now I cant get control of the background back, changing the settings through xfce does nothing. any ideas?
thanks

---

### Post by anarki on 2005-08-10
What about
killall nautilus

---

### Post by g7yh7uj8k on 2005-08-10
Thats the strange part, I killed nautilus right after it happened, the icons went away but the background stayed and the xfce right click menu is gone. when I reboot nautilus is not running but the desktop is still wrong.

---

### Post by astoltz on 2005-08-10
You've got to restart the xfce desktop.```
killall xfdesktop
xfdesktop &
```

---

### Post by g7yh7uj8k on 2005-08-10
ok
It  looks like xfdesktop and xfdesktop & are not starting on their own anymore.They were allready not running, so I started them and everything worked great, then I logged out and back in and they had not started.

---

### Post by Xterminator on 2005-08-10
run 

```
nautilus --no-desktop
```

or modify nautilus berhavior in **gconf-editor**

apps>nautilus>preferences

unmark **show_desktop**

;-)

---

### Post by v2.0 on 2005-09-28
come on. does anyone have a real answer for this? i installed xfce and xfdesktop never came up. of course i can run it from command line but i would like to correct the problem. any help would be awesome!

---

### Post by bourrinlepoulpe on 2005-09-28
hi excuse my imperfect english but you can to install the package gTweakUI
then in system -> preferences -> gTweakUI-nautilus you have to disable nautilus to draw the desktop ( i don't if it's traductible lik that ?)
it works for me on e17 when i launch nautilus

---

### Post by sameat on 2005-09-28
Start xfdesktop and then log out saving your session.

---

### Post by psychicdragon on 2005-09-29
Entering this command in the terminal will make sure that nautilus never takes over your desktop again. While still allowing you to use it for file management if you choose.
```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
```
Make sure you start xfdesktop up again afterwards if you haven't already.
I wouldn't bother with gtweakui personally, all the options it allows you to edit (and more) can be accessed through gconf-editor.

---

