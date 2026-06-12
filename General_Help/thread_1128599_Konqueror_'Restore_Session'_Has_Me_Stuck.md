---
title: "Konqueror 'Restore Session' Has Me Stuck"
date: 2009-04-17
forum: General Help
---

### Post by clk99 on 2009-04-17
You know that 'Restore session?' dialog box that comes up when you reopen Konq after it crashes--since it crashes *all* the time?  Well, I think I must have checked 'Do not ask again' one of the times it came up, because it recently crashed and when I reopen it it brings up all the tabs I had opened when it crashed.  The problem is that there must be something Konqueror doesn't like on one of the sites because it instantly crashes again.

Now I've had this happen before and managed to quickly close all the tabs before the pages load, but this time I'm out of luck.  There's too many tabs open for me to get at which ever one is the demon.

Even after rebooting this stays the same.  I can, however, open another instance of Konqueror while the bad one loads and this second one will be blank and usable, so I can get the browser open.  I've looked through all the settings and can't find a way to either re-enable the 'Restore session' dialog or to force a new session.

Anyone know how I can do this?  There must be some way to change my mind after checking 'Do not ask again.'  Right?

---

### Post by powder on 2009-04-17
You could try backing up your old profile, then start Konqueror with a new profile.  I think it would be something like this...

```
mv ~/.kde/share/apps/konqueror ~/.kde/share/apps/konqueror_backup
```

Now launch Konqueror again.

---

### Post by clk99 on 2009-04-17
I suppose I'll just do that and copy over my bookmarks.xml, but it'd be nice to know if there really is a way to change that session setting.

Thanks for the reply.

---

