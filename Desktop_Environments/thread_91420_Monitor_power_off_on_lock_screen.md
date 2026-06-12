---
title: "Monitor power off on lock screen"
date: 2005-11-17
forum: Desktop Environments
---

### Post by yaztromo on 2005-11-17
Hello

Is there some way to set X/Ubuntu to power off the monitor when I choose lock screen? At the moment it just blanks it.

edit: Or at least does anyone know a way to lock the screen via the command line? Then I could write a script which uses xset to power down the monitor and then locks the screen.

---

### Post by yaztromo on 2005-11-17
Okay found the solution myself.

Replaced the Lock Screen button with a button that runs this little script

#!/bin/sh
xscreensaver-command -lock && xset dpms force off

And voila! Screen locks and monitor powers down.

---

