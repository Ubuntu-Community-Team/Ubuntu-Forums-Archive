---
title: "Scripting Compiz enable/disable"
date: 2009-07-16
forum: Desktop Environments
---

### Post by darkknight045 on 2009-07-16
There are some games and functionality that I would like to be able to automate a bit. 

Is there a away to enable/disable compiz through bash commands so that upon the game closing I can signal for compiz to start back up with the settings it had before?

---

### Post by mcduck on 2009-07-16
Sure.

"metacity --replace" will replace your current window manager with Metacity, which is the default WM for Gnome. 

..and "compiz --replace" will then replace Metacity with Compiz.

---

### Post by finch127 on 2009-07-18
Yeah I actually wrote a script for this:

[http://ubuntuforums.org/showthread.php?t=1207203](http://ubuntuforums.org/showthread.php?t=1207203)

Check it out, if it is indeed what you need.

---

