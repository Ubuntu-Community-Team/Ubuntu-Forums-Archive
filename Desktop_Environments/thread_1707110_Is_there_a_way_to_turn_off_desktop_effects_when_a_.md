---
title: "Is there a way to turn off desktop effects when a specified program starts?"
date: 2011-03-14
forum: Desktop Environments
---

### Post by robro on 2011-03-14
Hello,
I'm looking for a way to turn off desktop effects (eg, composite) whenever a specified program starts, because whenever I play "heavy" games, the desktop effects slows them down considerably, I know of the alt+shift+12 keyboard shortcut but I forget 80% of the time to turn them back on after I'm done playing :lol:

Thanks for the help :)

---

### Post by robro on 2011-03-16
bump :(

---

### Post by mcduck on 2011-03-16
You could edit the program's launcher to do that.

For example, you can write a small script to switch window manager to Metacity, start your game, and after that change back to Compiz again. Then point the game's menu entry to that script instead of the game itself.
```

#!/bin/sh

metacity --replace
/path/to/yourawesomegame
compiz --replace
```

edit: I just misseed that you are using KDE. Well, the same method should work just fine, just use Kwin instead of Metacity... :)

---

### Post by ankspo71 on 2011-03-16
Hi,
Check to see if your version of KDE has the option to automatically suspend compositing with full screen windows. KDE 4.6.1 has this option located at System Settings > Desktop Effects > Advanced > "Suspend desktop effects for full screen windows". I don't think I remember seeing this option in KDE4.5.x though.

The following link has some KDE commands that can probably be used with mcduck's script example. See the fourth post here:
[http://forum.kde.org/viewtopic.php?f=111&t=6712](http://forum.kde.org/viewtopic.php?f=111&t=6712) 

If none of the above helps, maybe you could rename your your game's start menu entry to something like "Game Name Alt+Shift+F12" to remind you to toggle the desktop effects. ;)

Hope this helps.

---

### Post by robro on 2011-03-18
well the script didn't help much, for some reason it got stuck with no window manager... so I had to logout and back in again to get it right, unless someone can help again I'm just going to let this thread die and try to remember the shortcut :)

btw, if it helps, I'm using kde 4.5.1

---

