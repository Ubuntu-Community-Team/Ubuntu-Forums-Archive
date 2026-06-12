---
title: "Autostart app in xfce"
date: 2005-09-14
forum: Desktop Environments
---

### Post by rejser on 2005-09-14
Is there a quick way to add a script to the startup of xfce4?
Have different scripts for my mouse-buttons depending on which wm I use.
If I add to .xinitrc I can get one default, but don't wan't that.

/Oscar

---

### Post by psychicdragon on 2005-09-14
You could put a script in ~/Desktop/Autostart

---

### Post by rejser on 2005-09-14
[QUOTE=psychicdragon]You could put a script in ~/Desktop/Autostart[/QUOTE]

Isn't it only kde that uses that folder?

---

### Post by sameat on 2005-09-14
I run a couple of scripts in XFCE using this method.  Works fine.

---

### Post by rejser on 2005-09-15
[QUOTE=sameat]I run a couple of scripts in XFCE using this method.  Works fine.[/QUOTE]
  Hmmm... 
Have to try it...

---

### Post by Virtual DarKness on 2006-01-09
I've found another method that doesn't require to have the Autostart folder on the desktop..

[LIST=1]
[*]create the file **~/.config/xfce4/xinitrc** if it doesn't exists
[*]```
$ chmod +x ~/.config/xfce4/xinitrc
```
[*]edit the new file and in this way:
```
#!/bin/sh
# The scripts/apps you want to launch here (ending with " &"):
exec /usr/lib/vino/vino-server &

# The default startup script here (without the ending " &"):
exec /etc/xdg/xfce4/xinitrc
```
[/LIST]

seems to work for me; I hope you'll find it useful.
Keep in mind that you did this change if you will have some kind of problems at startup expecially when new xfce version or ubuntu will be released ;-)

bye,
Giovanni.

---

