---
title: "OPEN-Box, ROX-Session, Autostart  Help!"
date: 2009-02-12
forum: General Help
---

### Post by n2stc on 2009-02-12
I am running openbox with the rox manager.  I'd like to have some apps start upon login, but can't get it.  The little autostart app runs, and I found where the apps displayed are stored.  When I copy a new file into there, it doesn't run at log in.  Where should the AUTOSTART apps/folders/desktops be stored?

Thanks,

Stan

---

### Post by n2stc on 2009-02-12
Boldly bumped!

---

### Post by spcwingo on 2009-02-12
Try ~/.config/autostart/  I didn't have a folder named autostart, so I created one and placed the .desktop file of the app I wanted to autostart in there.  I haven't tried it on pure openbox, but it works great on LXDE, which uses openbox as a WM.

---

### Post by n2stc on 2009-02-12
> **spcwingo said:**
> Try ~/.config/autostart/  I didn't have a folder named autostart, so I created one and placed the .desktop file of the app I wanted to autostart in there.  I haven't tried it on pure openbox, but it works great on LXDE, which uses openbox as a WM.

I dragged a link to that folder: No Go.  I've seen .desktop files, but I can't remember where or how they were created.  I guess I'm messing with too many different apps.

Thanks!

---

### Post by n2stc on 2009-02-12
I found the .desktop files.  They don't do it either.  :(

---

### Post by m_duck on 2009-02-12
If you want an app to start when you log in to openbox, just add it to the ~/.config/openbox/autostart.sh. E.g. if you want pidgin to start on login, add the following line to the aforementioned file:```
pidgin &
```This will work assuming openbox is launching with openbox-session...

[Autostarting in openbox](http://icculus.org/openbox/index.php/Help:Autostart)

---

