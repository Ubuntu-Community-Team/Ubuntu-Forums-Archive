---
title: "Faulty Session Management"
date: 2005-10-15
forum: Desktop Environments
---

### Post by berserker on 2005-10-15
I have "Start with an empty session" selected in KDE Components/Session Manager of the KDE Control Panel.

I log off with no application windows open.

However, whenever I login to KDE a Kate window pops up with a file I was working on last week.  I don't recall if KDE froze while I was working on it but it's possible.

Is there a file I can delete or modify to keep this Kate window from popping up every time I login to KDE?

TIA

---

### Post by daller on 2005-12-01
What happens if you choose "Restore saved session", and then saves an "empty" session?

---

### Post by berserker on 2005-12-01
[QUOTE=daller]What happens if you choose "Restore saved session", and then saves an "empty" session?[/QUOTE]

Thanks for the reply.  I tried that with no luck.  I finally figured out that somehow the file was invoking Kate on startup.  I moved the file and the problem went away.

---

