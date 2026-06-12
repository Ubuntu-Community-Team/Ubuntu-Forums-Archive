---
title: "Lucid Logout Confirmation"
date: 2010-08-27
forum: Desktop Environments
---

### Post by scottyo on 2010-08-27
I want to get rid of the logout/shutdown/restart confirmation dialog. I have searched in the forums and have not found a solution.  Is there a way to avoid the "are you sure" box in gnome in lucid ubuntu? Thanks.

---

### Post by pastalavista on 2010-08-27
Run [Alt+F2] gconf-editor and open apps/gnome-session/options and uncheck the box beside logout_prompt.

---

### Post by scottyo on 2010-08-27
Thanks! very helpful!!

Actually the apps -> indicator-session was the one I needed. (I was using indicator-applet to logout). But checking the suppress_logout_restart_shutdown did the trick!   Thanks again - I never would have found that without your suggestion.

---

