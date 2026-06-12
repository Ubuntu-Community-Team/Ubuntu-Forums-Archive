---
title: "Default window size?"
date: 2007-05-28
forum: Desktop Environments
---

### Post by drpynchon on 2007-05-28
Just wondering,

Is there a way to easily control the default window size? This is of particular concern for me with Firefox, which always opens up at the same size, and a bit small for my liking. I've tried the command line arguments of -width or -height and those seem to do nothing. If it matters, I'm using Feisty with gnome, beryl, and xfdesktop in place of nautilus.

Any help would be much appreciated.

---

### Post by sankarv on 2007-05-28
hi just adjust the size of firefox in non-maximized mode as you wish and close it and reopen . it will be in the size u chosen itself. its not looking successful in command line as i too tested that..

---

### Post by drpynchon on 2007-05-28
That doesn't work for me. Regardless of what the size of the last closed Firefox window was, all windows open at the same size.

---

### Post by drpynchon on 2007-06-03
Found the fix myself. Something was wrong with the localstore.rdf file in my Firefox profile directory (~/.mozilla/firefox/xxxxxxx.default/localstore.rdf). I just deleted it and restarted FF and the problem was solved. Now windows size to the last closed window size.

---

### Post by coldstatue on 2007-06-05
thisworks for me until I reboot. Sunbird, Firefox, and Thunderbird all default to the maximized window size even when not maximized. I have to resize them to their "restore" size. They don't remember it.

---

