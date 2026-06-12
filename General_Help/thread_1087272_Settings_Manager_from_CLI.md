---
title: "Settings Manager from CLI?"
date: 2009-03-04
forum: General Help
---

### Post by solwic on 2009-03-04
This is probably a really dumb question, but how can I access Xubuntu's settings manager (Applications -> Settings -> Settings Manager) from the command line?  Basically, I'm wanting to create a panel shortcut to it, and need the command.

Also, is there some easy way of finding these commands that I don't know about?

Thanks!

---

### Post by sisco311 on 2009-03-04
i think it's xfce-mcs-manager. 

in xfce 4.6 it's xfce4-settings-manager.


start the app and type "ps -ef" in a terminal to list the running processes.

---

### Post by solwic on 2009-03-04
> **sisco311 said:**
> i think it's xfce-mcs-manager. 

in xfce 4.6 it's xfce4-settings-manager.


start the app and type "ps -ef" in a terminal to list the running processes.

Well the command "ps -ef" gives me ```
james     6303     1  0 19:43 ?        00:00:03 xfce-mcs-manager
```

But when I plug that into the panel shortcut and click it, nothing happens.  If I use the "xfce4-settings-manager" command it tells me it doesn't exist.  

:confused:

EDIT:  Do I need the exact path here?  Like /usr/whatever/xfce-mcs-manager ??

---

### Post by 4Orbs on 2009-03-04
xfce-setting-show

You can find the command for any app by opening the xfce Appfinder, then right click on an app and select "More Information"

---

### Post by Iowan on 2009-03-04
> **jrock612 said:**
> EDIT:  Do I need the exact path here?  Like /usr/whatever/xfce-mcs-manager ??I suspect you do.  **locate xfce-mcs-manager** *might* lead you to it.

---

### Post by solwic on 2009-03-04
> **4Orbs said:**
> xfce-setting-show

You can find the command for any app by opening the xfce Appfinder, then right click on an app and select "More Information"

Thank you and thank you!

Your command worked, and the Appfinder thing is awesome.  It's exactly what I was looking for.  

You rock, dude.  :)

EDIT:  Would mark SOLVED, if I could.

---

