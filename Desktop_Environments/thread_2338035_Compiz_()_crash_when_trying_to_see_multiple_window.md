---
title: "Compiz (?) crash when trying to see multiple windows of the same app in Ubuntu 16.04"
date: 2016-09-23
forum: Desktop Environments
---

### Post by gutierrez-rojo on 2016-09-23
[COLOR=#111111][FONT=Ubuntu]I installed Ubuntu 16.04 recently and the only problem I have right now is this glitch that doesn't let me see the other windows of the same app.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I click the icon so it shows me all the windows I have of that app it just crashes the UI and restarts again.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How can I fix it? If it can't be solved I'll have to install Ubuntu again and/or downgrade. Cheers.[/FONT][/COLOR]

---

### Post by CantankRus on 2016-09-23
Does the guest account behave the same?

---

### Post by gutierrez-rojo on 2016-09-23
No. I'm in the guest account right now and I'm not having any problems

---

### Post by CantankRus on 2016-09-24
OK, suggests it's a user config error.
The unity window manager (compiz) handles the window spread function.

Log into your regular account and reset compiz to defaults with this terminal command...
```
dconf reset -f /org/compiz/
```
Log out and back in and test.

---

### Post by gutierrez-rojo on 2016-09-24
Fixed! Thanks!

What could have possibly caused it? I played around with Unity Tweak Tool but I used it with 14.04 and didn't cause any problems. Thanks again!

---

### Post by CantankRus on 2016-09-24
Not entirely sure.
I use Unity Tweak Tool for some customization but for compiz settings I use ccsm (compizconfig-settings-manager).

---

