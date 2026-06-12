---
title: "How to make ClipMan start at login on Xubuntu"
date: 2022-06-23
forum: Desktop Environments
---

### Post by managerrose on 2022-06-23
I'm running Xubuntu 20.04. How do I make ClipMan start at login on Xubuntu 20.04?

---

### Post by TheFu on 2022-06-23
Is there an "autostart" option in any of the settings?  

I found the Xubuntu Desktop Guide [https://docs.xubuntu.org/2004/user/C/index.html](https://docs.xubuntu.org/2004/user/C/index.html), but it doesn't obviously have a section on setting this up.  For other light DEs, the window manager, wm, is where startup applications are setup.  For example, in the old Lubuntu, there's an autostart directory in $HOME/.config/autostart/  Where scripts and .desktop files can be linked.

Oddly, in that directory, I see a mention of xfce4-settings-helper. I'd try running that to see if it brings up a way to control startup applications.  Then just add the clipman application to the list.

---

### Post by &amp;KyT$0P# on 2022-06-23
There are two ways to do it:

1) enable/check it in Settings > Session & Startup > Application Autostart

or,

2) install [FONT=Courier New]xfce4-clipman-plugin[/FONT] package and add the Clipman plugin to one of your panels.

---

### Post by managerrose on 2022-06-23
Thanks. I used method 1 which worked. I'm so used to standard Ubuntu that I didn't notice Settings-.Session & Startup! 
BTW xfce4-clipman-plugin was already installed.

---

