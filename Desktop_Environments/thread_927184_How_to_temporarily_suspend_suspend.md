---
title: "How to temporarily suspend suspend?"
date: 2008-09-22
forum: Desktop Environments
---

### Post by gilgongo on 2008-09-22
I've been Googling for a while but I can't work out how to temporarily turn my suspend settings off when I launch an app.

For example, my normal setting (in Preferences > Power Management) is to suspend my machine after about 30 mins idle time. However, if I want to run an operation over night (in my case it's transcoding my camcorder tapes), I don't want it suspending during that time until I quit the app.

Of course, I could just remember to manually put the suspend setting to "Never." But I'd forget. I'm crap like that.

I'm thinking something like this:

```
dbus-send \
--session \
--dest=org.freedesktop.PowerManagement \
--type=method_call \
--print-reply \
--reply-timeout=2000 \
/org/freedesktop/PowerManagement \
org.freedesktop.PowerManagement.KillSuspendOffOK
```

But the last line needs to be correct, obviously :)

Does anyone know how?

---

