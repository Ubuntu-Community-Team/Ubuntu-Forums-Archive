---
title: "XFCE and autostarting applications"
date: 2007-02-04
forum: Desktop Environments
---

### Post by figgles on 2007-02-04
I have applications that are loading from previous sessions, despite the fact that I have disabled the "Save Session" checkbox at log-off and don't see these applications listed in the sessions > autostarted applications list.

Help and Thanks in Advance.

---

### Post by kerry_s on 2007-02-04
Select the save session then kill the application(killall (app "name") then log out and back in again, then uncheck the save session and out and in again. That should get you set on a clean session each time. You can also try  deleting the session cache(rm -r ~/.cache/sessions) or all the cache(rm -r ~/.cache), which will bring you back to stock.

---

