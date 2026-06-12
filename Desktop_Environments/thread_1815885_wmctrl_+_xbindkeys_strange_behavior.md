---
title: "wmctrl + xbindkeys: strange behavior"
date: 2011-08-01
forum: Desktop Environments
---

### Post by netwalkman on 2011-08-01
I use wmctrl and xbindkeys to quickly switch between windows. This is my .xbindkeysrc file
```

"wmctrl -xa Terminal || gnome-terminal"
Mod4 + T

"wmctrl -xa Firefox || firefox"
Mod4 + B

"wmctrl -xa gvim || gvim"
Mod4 + V

```

The keybindings work for the first few switchings, and then stop working. No such problem with Debian or Fedora. It may be caused by compiz, but I think there is no conflicting keybindings.

---

### Post by netwalkman on 2011-08-01
If this can't be fixed, is there a substitute?

---

### Post by enimeizoo on 2011-08-01
I have troubles with xbindkeys crashing, but I didn't find out why (looks random atm). Is xbindkeys still running when it stops working? 

To work-around, I have defined a custom kde shortcut that launches xbindkeys. It sure isn't the best solution, but it works fine.

---

### Post by netwalkman on 2011-08-01
It works now, except with Nautilus.
I added the following
```

"wmctrl -xa nautilus || nautilus"
Mod4 + F

```.

But it doesn't work at all.

---

### Post by netwalkman on 2011-08-06
Problem solved by building the newest xbindkeys from source.

---

