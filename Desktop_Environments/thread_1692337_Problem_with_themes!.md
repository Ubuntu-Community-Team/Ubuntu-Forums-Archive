---
title: "Problem with themes!"
date: 2011-02-21
forum: Desktop Environments
---

### Post by bilalsana on 2011-02-21
Hi
i have been having problems with themes, which ever theme i install there's a particular look to it that doesn't change! recently i tried the Orta theme and this is wat it looks like:[IMG]http://i.imgur.com/CQsi6.jpg[/IMG]
note the highlited items particulary!
how can i see the themes correctly?

---

### Post by Frogs Hair on 2011-02-21
Check out the solution posted on this thread , it may be related.[http://ubuntuforums.org/showthread.php?t=1692367](http://ubuntuforums.org/showthread.php?t=1692367)

---

### Post by bilalsana on 2011-03-02
didnt help!

---

### Post by stinkeye on 2011-03-02
Sounds like the common **gnome-settings-daemon** bug.
In the terminal run...
```
gnome-settings-daemon && killall nautilus
```

Adding **gnome-settings-daemon** to startup applications is
a temp fix to try, until they get around to fixing this long standing bug.

---

### Post by bilalsana on 2011-03-02
well i managed to solve the issue by deleting the .gtkrc-2.0 file in my home directory. seems like it was activating the gnome color chooser, which made all my themes look bad!

---

