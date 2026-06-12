---
title: "$MAIL env var not set in GNOME terminal"
date: 2010-02-27
forum: Desktop Environments
---

### Post by JohnE1 on 2010-02-27
Ubuntu 9.10 (upgraded from 9.04)

I can go to a virtual console (CTRL+F2), login, and if I echo $MAIL, I'm shown where my mail messages are kept.

johne1@pcss07~$ echo $MAIL
/var/mail/johne1

If I open a GNOME terminal and echo $MAIL it returns a blank line. Is there a reason the $MAIL environment variable is not passed to the shell running GNOME (or Metacity), or do I have a configuration problem?

TIA!

---

### Post by n0dix on 2010-02-27
You can set the variable, do the following:
```
export MAIL=/var/mail/username 
```
This is a temporary solution.

---

