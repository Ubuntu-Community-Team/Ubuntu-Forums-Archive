---
title: "In LUCID LYNX, how can I change the default Window Manager?"
date: 2010-06-14
forum: Desktop Environments
---

### Post by fivebells on 2010-06-14
I would like to change my default window manager to sawfish.  There are many instructions on the web to install sawfish, log out, then select sawfish, then log back in.  This worked for me with karmic, but I'm not seeing any way to select a window manager during the lucid log in process.  I'd appreciate some more details on how to do this.

(Sawfish is running fine if I start it with "killall compiz && sawfish &" during an ongoing session.)

---

### Post by gingivere0 on 2010-06-14
Whenever you about to log on, click on your name (or the name of whatever account you are trying to log on to) and before typing your password, look in the lower right side of the screen.  You should see a drop-down menu that says GNOME.  Click that and change it to sawfish.  Then log on.  If that doesn't work, idk what to do :/  Good Luck!

---

### Post by eggdeng on 2010-06-14
Maybe a little shell script along the lines of

```
#!/bin/bash
killall compiz && sawfish &
```

& then add it to Startup Programs in Preferences -> Startup Applications.

---

