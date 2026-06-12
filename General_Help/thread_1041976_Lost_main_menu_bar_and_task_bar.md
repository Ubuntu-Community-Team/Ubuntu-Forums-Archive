---
title: "Lost main menu bar and task bar"
date: 2009-01-17
forum: General Help
---

### Post by CharlesWaterhouse on 2009-01-17
I have a dual boot 8.10/XP machine.  Tried to boot 8.10 today but only get desktop background - no main menu bar or bottom task bar. 8.10 seems to be loaded as F1 brings up the normal help menu. Cannot switch off & reboot without pulling the plug. Repeated attempts to reboot that way don't solve problem. Monitor appears OK and machine will boot into XP to give normal XP desktop. Would much appreciate guidance as cannot bear the thought of going back to XP!

Charles Waterhouse

---

### Post by niklinux03 on 2009-01-17
Hi,

I suggest that you right click your mouse on
your desktop. You should see then a menu with
an entry called "Create Launcher.." - click this one.

Then enter as name of your launcher Terminal or whatever you like.
In the entry command enter

```

gnome-terminal

```

This will give you an icon to start a terminal.
Start it now.
Then enter in your console
```

gconftool -s /apps/panel/toplevels/top_panel_screen0/orientation --type=string top

```
To create the bottom panel enter in your terminal
```

 gconftool -s /apps/panel/toplevels/bottom_panel_screen0/orientation --type=string bottom

```
If your settings of gnome are okay in .gconf/, these are created
automatically during installation, then a panel should appear.
If this isn't the case, please post again.

Cu

---

### Post by niklinux03 on 2009-01-17
Hi again,

with respect to your problem switching off your maschine.
You can do the following.
Start the terminal as I suggested in my previous post.
Enter in the terminal
```

sudo shutdown -h now

```
Now enter your password.
This command will halt your system.
If you want to reboot then enter instead of -h the flag
-r.

Bye

---

### Post by CharlesWaterhouse on 2009-01-17
Thanks. Right clicking brings up the menu OK but clicking "Create Launcher" doesn't produce another screen.

---

### Post by niklinux03 on 2009-01-17
Hi,

well, your gnome installation seems to be broken.
You have the option to try pinpointing the cause of this.
To do so, you have to switch to a console via CTRL+ALT+F1
and start the research...

But if you don't have the time or you don't like this idea,
the only thing I can recommend you is to install 8.04
or 8.10 again.   

Bye

---

### Post by CharlesWaterhouse on 2009-01-28
Belated thanks niklinux03 - I had to reinstall.
Cheers

---

