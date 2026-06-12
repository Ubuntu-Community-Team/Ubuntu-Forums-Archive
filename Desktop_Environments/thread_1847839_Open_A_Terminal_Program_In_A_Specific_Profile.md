---
title: "Open A Terminal Program In A Specific Profile?"
date: 2011-09-21
forum: Desktop Environments
---

### Post by dniMretsaM on 2011-09-21
I have an application launcher on a panel for Vim, which runs in Konsole. However, I have a profile I like to use for Vim, but when I click on the launcher, it opens in the default "Shell" profile. So my question is, how can I change it to open in my "Vim" profile? Edit Launcher... -> Application -> Advanced Options has a box for Terminal options and I thought maybe I need to put something in there, but I have no idea what it would be.

---

### Post by dave01945 on 2011-09-21
i'm not sure about kde konsole but it should have a similar option

with gnome-terminal there a command line switch to choose a profile check the man page for konsole and see if it has a similar option then add that to the launcher

---

### Post by dniMretsaM on 2011-09-21
> **dave01945 said:**
> i'm not sure about kde konsole but it should have a similar option

with gnome-terminal there a command line switch to choose a profile check the man page for konsole and see if it has a similar option then add that to the launcher

```
~$ man konsole
No manual entry for konsole
```Sigh... Google time. :p

EDIT: Ok, found it. Added [FONT=Courier New]--profile Vim[/FONT] to the Terminal options and it worked great. Thanks.

---

