---
title: "remote desktop XRDP LXDE (GDBUS.Error: org.freedesktop.PolicyKit1.Error.Failed)"
date: 2014-12-15
forum: Desktop Environments
---

### Post by stkeg on 2014-12-15
i'm running ubuntu 14.04.1 LTS. i have lubuntu-desktop and xrdp installed.

when i start a remote session i'm getting a pop up error:

GDBUS.Error: org.freedesktop.PolicyKit1.Error.Failed:Cannot determine user of subject

i don't have lxpolkit installed or running. polkitd is running though.

anyone know what could be the solution?

---

### Post by drexlock on 2015-05-12
Sorry to necro thread but im running into this same issue. Cant for the life of me figure out how to pin it down

---

### Post by steveferson on 2015-12-08
I'm having this same issue and have been since I installed XRDP on Lubuntu.  Given that this seems to be related to authenticating the session I think this is also why tasks that require elevation (e.g. running software updates when the update notifier pops up) aren't working.

Still not sure where to go to fix this but going to try some more digging.

---

