---
title: "CTRL+ALT+Function key doesn't change console"
date: 2007-03-26
forum: Desktop Environments
---

### Post by blagger on 2007-03-26
hi all,

i have a ubuntu dapper server installed, and then i decided to add the necessary packages so i can have a Xorg+Gnome desktop.

the problem is simple, i can't change to my text consoles via pressing CTRL+ALT+F1 , CTRL+ALT+F2 ....

how can i solve that?

---

### Post by blagger on 2007-03-28
Well, finally I've found the solution.

Googling these days shows me that there are many people with this issue, but, the solution is simple:

# apt-get install xkbutils xkeyboard-config

It seems that /etc/X11/xkb/symbols/pc is a file provided by xkeyboard-config where are listed the shortcut keys and actions. Then, xkbutils, provides the tools to work with these keys and actions.

Hope this solution can help someone in the future...

---

