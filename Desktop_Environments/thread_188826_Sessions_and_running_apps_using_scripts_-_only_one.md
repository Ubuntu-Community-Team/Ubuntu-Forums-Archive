---
title: "Sessions and running apps using scripts - only one script works :/."
date: 2006-06-04
forum: Desktop Environments
---

### Post by Teo on 2006-06-04
I need to run some apps using script files put in System -> Preferences -> Sessions ex: 'sh ~/.aMule/run.sh', 'sh ~/.gg/run.sh' etc...

But there's something wrong - Gnome start only one script, rest of them won't (wasn't issue in Breezy - all of them started).

Scripts are write correctly and working when run by hand in terminal.

example script:
```
#!/bin/sh
sleep 10
amule
```

I need to use that scripts - without them Gnome won't put app tray icons into Notification Area (don't know why they start before Notification Area Applet - it's issue not only in Ubuntu but in Gnome in general).

---

