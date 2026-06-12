---
title: "removing shutdown from menus"
date: 2014-08-27
forum: Desktop Environments
---

### Post by Rgc183 on 2014-08-27
I want to remove shutdown, restart and all other menus except logout from UI on desktop. I want to keep them only for root or particular user. How can I do that?

---

### Post by gdesilva on 2014-08-28
Just in case if you are using XCFE it can be done simply by clicking on the Panel -> Preferences -> Items -> Actions. Then click on edit and then you can turn on or off various options. Not sure how this can be done in Unity.

---

### Post by vasa1 on 2014-08-28
> **Rgc183 said:**
> I want to remove shutdown, restart and all other menus except logout from UI on desktop. I want to keep them only for root or particular user. How can I do that?
Won't you have to restrict access to sudo as well?

And then a user could use something like this (which is what I use):```
#!/usr/bin/env bash

zenity --question --text="Proceed to shutdown?"
if [ $? = 0 ]; then
    dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
else
    exit
fi
```And what happens if the user just presses the power button?

---

### Post by deadflowr on 2014-08-28
If on ubuntu, perhaps dconf editor(from the package dconf-tools) >> apps > indicator-session.
this should have a bunch of options to suppress shutdown restart ,et cetra et cetra.

The problem is, this is set per user, so you would have to run it for each...

---

