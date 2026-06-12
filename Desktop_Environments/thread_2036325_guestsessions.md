---
title: "guestsessions"
date: 2012-08-01
forum: Desktop Environments
---

### Post by Ofloo on 2012-08-01
I recently changed from ubuntu to xubuntu up until now, most of the things work like i want however, .. there is one that i really liked in ubuntu which doesn't seem to be on xubuntu, and that's guest sessions, .. in ubuntu i could guest session from my user account without logging out, .. now i was wondering how this can be done in xubuntu,... cause i really liked that feature especially when my kids wanted to do something on my computer i'd just give them the guest and no harm done right, .. 

so how do i do this in xubuntu, ... 

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

---

### Post by Toz on 2012-08-01
Here is one way to get this to work on Xubuntu:

1. Create a new launcher called "Guest Login"
2. For the command, enter:
```
/usr/lib/lightdm/lightdm/gdmflexiserver
```
...(select whatever icon you want)
3. Click on the launcher to create a new X session. From there you will get a second X session with a lightdm login where you can login as Guest. Note that this session will appear on the 8th tty ( Ctrl+Alt+F8 ).

---

