---
title: "Screen res won't stick Jaunty 9.04"
date: 2009-04-28
forum: Desktop Environments
---

### Post by timstone on 2009-04-28
I keep having to change my screen res back to 1280x1024 each time I reboot.  I've changed it in nvidia x server several times and even manually changed the xorg.conf with no luck.  The screen keeps reverting back to 1152x864....I know the monitor is capable of 1280x1024 because thats what I use when running windows.

The monitor is a Dell E773c and the gpu is nvidia 7300 GT

---

### Post by Dark Hornet on 2009-04-29
It sounds like you need to make the changes as root...try opening up your nvidia settings as sudo.  Once you have made your changes, make sure you click on the button that saves it to your xorg.conf file.  I can't remember exactly what its called, as I am not in front of my home pc at the moment.  At any rate, good luck!

---

### Post by timstone on 2009-04-29
i cant even save the xorg.conf while using the x server program i keep getting this error

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

thats why i tried to edit the file manually and it still keeps switching back to the lower resolution

ive even tried using

xrandr -s 1280x1024 -r 50

that didnt work either :(

---

### Post by timstone on 2009-04-30
anyone have a fix for this?  ive tried to run xrandr -s 1280x1024 -r 50 as a startup command but when i do that i end up getting these gray boxes in certain spots on my screen

---

