---
title: "Question regarding Wine/Ubuntu"
date: 2009-01-10
forum: General Help
---

### Post by Keikowned on 2009-01-10
Let's say that I accidentally executed a keylogger in the emulated wine desktop, does that "keylogger" only record keystrokes from programs under wine, ubuntu, both, or none? 

Would the solution be to re-install wine?

Thanks in advance ``

---

### Post by Keikowned on 2009-01-10
> **Keikowned said:**
> Let's say that I accidentally executed a keylogger in the emulated wine desktop, does that "keylogger" only record keystrokes from programs under wine, ubuntu, both, or none? 

Would the solution be to re-install wine?

Thanks in advance ``

:confused:

---

### Post by snova on 2009-01-10
I don't know...

If you want to make sure it's gone, I would recommend removing the ~/.wine directory. Wine stores all its files there.

And 45 minutes is hardly long enough to necessitate a bump. ;)

---

### Post by mgol on 2009-01-10
If you didn't run wine as root (as default you don't) it shouldn't affect any application run outside of wine. Re-installing wine won't remove Your ~/.wine configuration folder, so this is not the solution.

Make sure if You're aware of what You're doing - if You follow this step, **You'll lose all configuration of programs installed in wine and those programs itself**, too. You'll have to install and configure them again.

You should turn off Your wine and make sure it's not running, by typing:
```
 ps -e | grep wine
```
If this command returns no lines, then wine is not run. Then execute (**be warned of what I said before!**):
```
 rm -rI ~/.wine
```
It will only once ask You for confirmation and then delete all wine data. Then You can install all Your wine applications again, it should be safe now.

---

