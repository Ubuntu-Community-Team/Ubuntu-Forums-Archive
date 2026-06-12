---
title: "Compiz problem: display &quot;:0.0&quot; already..."
date: 2006-08-16
forum: Desktop Environments
---

### Post by camtech on 2006-08-16
I am atempting to get xgl and compiz runnig using this guide: 
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)
I am using method B since method A didnt exactley work (ask me for details).  Anyway after I have restarted (at the end of method B) I ran the compiz file from the desktop in terminal and got this reponse:
```
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration mana
ger; try using the --replace option to replace the current decoration manager.
compiz.real: No composite extension
```

It does say "try using the --replace option" but being a linux newb I have no idea where.:confused: 

All the compiz file contains is, as the guide shows:
```
#!/bin/bash
#killall xfwm4 #XFCE users, uncomment this line
gnome-window-decorator &
compiz --replace gconf &
xmodmap -e "keycode 22 = BackSpace Delete"
```

Any suggestions or pointers are appreciated.

---

### Post by chalex on 2006-08-16
You should probably look at the forums at compiz.net.

I see two problems right away: you're missing a line "killall gnome-windows-decorator" and I think "compiz --replace" is now replaced by "cgwd" or something.

---

