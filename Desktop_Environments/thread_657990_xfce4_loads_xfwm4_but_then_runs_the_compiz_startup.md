---
title: "xfce4 loads xfwm4 but then runs the compiz startup script"
date: 2008-01-04
forum: Desktop Environments
---

### Post by jw5801 on 2008-01-04
I have a 7.10 Ubuntu install, so I use gdm as my login manager and have used Gnome+Compiz for a reasonable amount of time. I've recently been playing around with a few desktop environments, and have decided that I like the look of Xfce and have been using that fairly regularly. However, I have noticed every time I login, the compiz startup script is run, as it should have were I to login to Gnome. This results in me needing to kill compiz.real and start xfwm4 (it's odd that it doesn't have a "--replace" option...) every time I login.

I'd like to keep compiz running under gnome so I can't simply uninstall it, however I'd like to stop the script running whenever I login to Xfce. I've tried ticking the "save session" box when I log out but that doesn't seem to have any effect. Compiz isn't listed in the Xfce "Autostarted Applications," so I'm not entirely sure what's calling it or how to stop it. xfwm4 loads when I login (as expected), however it is overridden by compiz shortly thereafter, just like during a gnome login. Does anyone have any idea where I can look to try and stop this?

---

### Post by jw5801 on 2008-01-05
Bump?

---

### Post by yourpalal on 2008-01-05
try changing you settings under gnome so that Compiz is not run on startup... perhpas this will

---

### Post by jw5801 on 2008-01-05
Having the command present (but with it's box unchecked) in the Gnome "System>Preferences>Sessions" menu, causes it to still be run under Xfce (but not under Gnome), removing it completely stops it from running in Xfce. Obviously having it checked runs it under both. I'll note that in none of these cases is the command present in the Xfce "Settings>Autostarted Applications" menu.

Removing the entry fixes the problem for now, while I'm mostly using Xfce, but I'd still like to have the command run automatically under Gnome and not under Xfce, if anyone knows how this would be possible?

---

