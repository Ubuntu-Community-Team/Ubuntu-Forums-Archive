---
title: "Plasma hangs on login"
date: 2010-11-04
forum: Desktop Environments
---

### Post by lykwydchykyn on 2010-11-04
I have an annoying issue with plasma-desktop since upgrading my 64bit kubuntu 10.04 to Maverick.  Whenever I login, plasma-desktop hangs and my desktop/panels/plasma-whatevers never show.  I have to open a konsole, kill the plasma-desktop process, and rerun manually.  Then everything comes up just fine.

It doesn't happen on a fresh account, so I guess it is something in my configuration, but I really don't want to wipe my configs and start over.  Any advice?

EDIT: found this in my .xsession-errors:
```

QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
QDBusObjectPath: invalid path ""
<unknown program name>(1860)/: Communication problem with  "plasma-desktop" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, t$


```

---

