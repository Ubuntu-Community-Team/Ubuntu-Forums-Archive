---
title: "make compiz run on startup"
date: 2008-11-02
forum: Desktop Environments
---

### Post by scriptox on 2008-11-02
hey

I recently installed xubuntu as my desktop environment, then I installed compiz-fusion for some cool effects. Everything works great, I just don't know how to make comp-fusion start on startup. People say to go to System > Preferences, but I can't do that in xubuntu. Any suggestions?

---

### Post by Blackwolf_Oz on 2008-11-03
To autostart compiz edit your session file:

Code:

gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc

and replace
Quote:
Client0_Command=xfwm4
with
Quote:
Client0_Command=compiz

---

