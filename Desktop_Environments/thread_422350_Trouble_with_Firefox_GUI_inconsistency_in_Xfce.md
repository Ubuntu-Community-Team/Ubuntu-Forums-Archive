---
title: "Trouble with Firefox GUI inconsistency in Xfce"
date: 2007-04-25
forum: Desktop Environments
---

### Post by wingedpig on 2007-04-25
You can see Rhythmbox in the back respecting the Xfce UI font preferences, but Firefox/Swiftfox wants to do its own ugly thing with large menu text and weird anti-aliasing.

FF looks perfect in Gnome, but atm it doesn't want to play well with Xfce

I need help solving this little annoyance please
EDIT: weird thing is that FF's companion Thunderbird looks perfect in Xfce

---

### Post by tommie74 on 2007-05-05
The problem is with Firefox, not the system. Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

