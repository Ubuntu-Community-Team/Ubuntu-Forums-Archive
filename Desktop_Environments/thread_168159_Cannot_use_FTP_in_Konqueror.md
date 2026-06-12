---
title: "Cannot use FTP in Konqueror"
date: 2006-04-30
forum: Desktop Environments
---

### Post by firecrotch on 2006-04-30
I can't use Konqueror as an FTP client anymore for some reason.  Worked just fine a few hours ago, and I've made no changes to any settings or anything.  Also, I'm sure that I can access the server, as I can access with FireFTP.  It (Konqueror) just sends my login information, then stops.  Any idea why?

UPDATE: The status bar just says "Connected to host", and it acts as though it is sending information, but it's not doing anything.

---

### Post by Kethinov on 2006-04-30
This happened to me recently. I use Kate in GNOME which has Konqueror integration. I simply opened up the task manager and started killing every KDE process I could find. I then restarted Kate and FTP worked again.

In your situation, I would recommend logging out of KDE, logging into some other desktop environment or window manager, bringing up a task manager, and killing every KDE process you can find, then log back into KDE.

Or simply reboot.

I think it has something to do with some KDE process going nutso on you. A bug in a recent Kubuntu lib build perhaps.

---

### Post by firecrotch on 2006-04-30
Thanks for the fast response! Simply rebooting solved it, though I had rebooted several times without it fixing it.  Weird.

---

