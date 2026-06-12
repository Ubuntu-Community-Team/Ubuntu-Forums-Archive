---
title: "error message, regarding keyboard layout"
date: 2006-02-04
forum: Desktop Environments
---

### Post by hazica on 2006-02-04
here's my issue:
I wanted to add another keyboard layout, which apparently isn't available in ubuntu. I downloaded an archive containing a file and the instructions telling me where to put this file. I undertook this daring manoeuvre a couple of weeks before christmas, and I don't remember what file it was or the path to it. What I do remember is that i had to overwrite another file and I made a backup copy before overwriting it. After restarting my machine, I got the error message
"[B]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/B]"
and now I can't even switch between the english and german layouts, which used to work before I attempted installing the third one.
Of course I tried replaceing the file I had overwritten with the backup copy, but it didn't have any effect whatsoever.
Oh.. and the layout I downloaded was from some ubuntu location, so I thought it was "safe".
What could/should I do in order to get rid of this stupid message and to get the different layouts working properly again?
thanx, max

---

