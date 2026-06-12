---
title: "How do you disable compiz in a terminal?"
date: 2009-02-24
forum: General Help
---

### Post by destructaball on 2009-02-24
Recently while playing around with some effects I chose a certain effect which crahsed my computer, now whenever I log in to any sort of session it just freezes then sends me back to the login. I've tried all of the different sessions and only the terminal works. Does anyone know how to turn off compiz effects for one session. Any help is appreciated

---

### Post by ibuclaw on 2009-02-24
Press **Ctrl+Alt+F1** and login to your account using your usual username and password.

Then type in:
```
gconftool -s /desktop/gnome/applications/window_manager/default -t string "/usr/bin/metacity"
```
and press **Enter**

This will set the default window manager back to the Ubuntu default (Metacity).

Then logout by pressing **Ctrl+D** and switch back to the gdm login screen ( **Ctrl+Alt+F7** )

And this time you should be able to login without issues.

Regards
Iain

---

### Post by destructaball on 2009-04-11
Thanks a lot man I was pretty dammed stuck there

---

