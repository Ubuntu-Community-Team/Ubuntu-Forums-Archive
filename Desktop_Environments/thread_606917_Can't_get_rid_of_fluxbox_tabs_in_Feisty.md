---
title: "Can't get rid of fluxbox tabs in Feisty"
date: 2007-11-08
forum: Desktop Environments
---

### Post by benton on 2007-11-08
Hi there, I installed fluxbox in Feisty and can't get rid of the tabs. In the menu I went to Configuration / Tabs in titlebar and disabled them. Restarted fluxbox and tabs still show. Then edited ~/.fluxbox/init and did set session.tabs to false. Restarted fluxbox and tabs still show. 

Anyone with the same problem? Any hints?

Regards,

-Benton

---

### Post by RedSquirrel on 2007-11-08
You want to *enable* Tabs in titlebar. That way, the will be in the titlebar and not sticking up on top.

The init file line should look like this:

```
session.screen0.tabs.intitlebar:        true
```

But it's just easier to do it through the menu:

Fluxbox menu -> Configure -> Tab Options -> Tabs in Titlebar

After you do that, there should be a little indicator (a square, most likely) showing that the tabs are supposed to be in the titlebar.

---

### Post by benton on 2007-11-08
Thanks a lot! That worked.

---

