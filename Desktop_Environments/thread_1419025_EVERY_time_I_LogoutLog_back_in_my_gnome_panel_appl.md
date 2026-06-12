---
title: "EVERY time I Logout/Log back in my gnome panel applets rearrange"
date: 2010-03-01
forum: Desktop Environments
---

### Post by amillionsheep on 2010-03-01
I'm not referring to the icons in the notification area, I am referring to all of the applets on my panel (aside from main menu and window picker, they seem to not move). I've tried right clicking and selecting 'Lock to Panel'. I have also tried Alt+F2 gconf-editor > apps > panel > global and selecting 'locked_down', and still when I login, all but my main gnome menu and window picker, are in random order.

Applets used:
2 x separators
Lock Screen
Clock
Notification Area
Indicator Applet Session

I have see some python scripts that force it to rearrange back to the way you want it, however, I just want to keep it from rearranging in the first place.. I can post a screenshot if need be.

Any ideas?

---

### Post by jamfreak on 2010-03-01
Hey, what's the python script you are using? I'm having the same problem and it's VERY annoying.Googled it but couldn't find a solution anywhere. This is definitely a HUUUGE minus for Ubuntu I think. Specially since the bug has been around for years....

---

### Post by amillionsheep on 2010-03-02
I'm not using any script. I just saw it somewhere on this board. I just arrange it how I like and then hibernate vs. shutdown. ;/

But like you said, you would figure they'd have fixed this by now. It can't be that hard. Remember what applets are where.. ffs

---

### Post by Coder543 on 2010-03-08
*Please*, go shout your grievances in the streets. (or Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082) ) I'm sick and tired of this bug, and its been around for at least 4 years. Its time to close that bug.

---

### Post by oakgrove on 2010-04-10
Here's how I fixed the "floating applets" issue. Change your resolution to the highest your monitor supports, fix your applets how you want them, then open a terminal and go to the ~/.gconf/apps/panel directory. When you get there:
```

$ sudo chattr -R +i *

```
This will make every file in that directory immutable even by root so gnome won't be able to change the panel settings on its own. If you need to make any changes to the panel later, undo this by:
```

$ sudo chattr -R -i *

```
in that same directory.

---

