---
title: "Unminimized window shows under the active window"
date: 2017-03-15
forum: Desktop Environments
---

### Post by Zatnaktel on 2017-03-15
Hi,
I had this problem in 16.04 and after upgrade to 16.10 are no fixes yet.

So, when I "unminimize" any window from panel (like closed but still running transmission or music player), it shows under the active window. I think that every version before shows each minimized window on the top, doesn't it?
It's awful. When I want to find it by Alt+Tab, it's at the end of list. Have you ever seen it? Any ideas how to fix it?

I tried Ubuntu Tweak, but i didn't find something like that and I don't know how to work with CompizConfig Settings Manager.

Thank you,
Zatnaktel.

---

### Post by ajgreeny on 2017-03-15
Do a search in **CompizConfig Settings Manager** for **focus** or **window focus** to see if that finds any settings you can change.
I do not use unity or compiz so have no way to test this but such settings are usually managers by the **window manager** in systems; ie compiz in Ubuntu with unity.

---

### Post by Zatnaktel on 2017-04-05
Yeah, exactly solution is
compizconfig&#8594;general options&#8594;focus&raise&#8594;focus prevention&#8594;off

Thank you for your answer, ajgreeny. :)

---

