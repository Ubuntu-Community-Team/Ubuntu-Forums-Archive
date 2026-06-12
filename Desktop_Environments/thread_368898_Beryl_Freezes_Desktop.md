---
title: "Beryl Freezes Desktop"
date: 2007-02-23
forum: Desktop Environments
---

### Post by bobshowrocks on 2007-02-23
Hey, I installed Beryl on to my Edgy Eft install, version 0.20 I think. I set it up to load in the sessions menu. Now when ever I log in the desktop freezes if I click or move my mouse over a menu. Is there some way I can remove beryl from the session menu through the terminal?

---

### Post by haricharan on 2007-02-23
Press Ctrl+Alt+F6...login with your username and password and type 
```
killall beryl
killall beryl-manager
```
and press Ctrl+Alt+F7 to go back to normal screen...
Open up Sessions from System and remove Beryl from startup. This should help you out

---

### Post by bobshowrocks on 2007-02-23
Thanks! That did the trick.

---

### Post by haricharan on 2007-02-24
u r welcome [:)]....i too experienced the same thing...we have to wait until beryl is releasing their stable version 0.2

---

