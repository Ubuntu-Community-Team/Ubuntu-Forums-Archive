---
title: "How to clean out KDE4 sessions?"
date: 2009-11-11
forum: Desktop Environments
---

### Post by antonpiatek on 2009-11-11
I recently upgraded from Jaunty to Karmic and now have ~25 kdesudo windows popping up on login. Each one says that the arguments were invalid... 
Where can I find the session file that is presumably the cause of these launches?

---

### Post by lovinglinux on 2009-11-11
System Settings >> Advanced User Settings >> Autostart

---

### Post by antonpiatek on 2009-11-11
> **lovinglinux said:**
> System Settings >> Advanced User Settings >> Autostart

I see 1 desktop files and 1 scripts - none of which look related to the ~25 kdesudo dialogs I get at startup

I suspect it is cruft in my saved session, rather than configured auto starts. I cannot find a kde session editor to see what is set for my current session

---

### Post by antonpiatek on 2009-11-11
I found the following file has kdesudo in it (via a grep -R):
~/.kde/share/config/ksmserverrc

removing that file and rebooting (twice!?) means I now have a cleaner session at login

---

