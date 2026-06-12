---
title: "panel problems: can't find something"
date: 2007-12-13
forum: Desktop Environments
---

### Post by TheMouse on 2007-12-13
I've lost the thing on the panel that shows internet connections. Not the Network Monitor. I'm not sure what it's called. By default, it looks like four bars. The stronger your connection, the more bars are coloured in. When you click on it, you can see the wireless networks available.

I just cannot figure out how to add it back to the panel. Help?

---

### Post by NilsE on 2007-12-13
The application is the Network Manager.  The executable is nm-applet.

However, what you are probably missing is the notification area so right click on the panel, select add to panel, and add the notification area.

If that is not it for example if you still see you battery state or the bluetooth icon you may not have nm-applet starting  at boot so go into Preferences > sessions and see if nm-applet (network manager) is there and selected.

You can also test that by going into a terminal and typing

sudo nm-applet 

and see if it shows up.

By the way, if you changed your icon theme it may just be a different looking icon instead of the 4 vertical bars so mouse over all the icons and see what they are. If it is there it will say "wired (or wireless) network connection.

---

### Post by Technophobia on 2007-12-13
I guess the easiest way would be right clicking the panel and select "Add to Panel".

Scroll down to System & Hardware and select "Network Monitor"

Click Add

---

### Post by TheMouse on 2007-12-13
NilsE:

Thank you. That worked perfectly.

---

