---
title: "problem with tar backup"
date: 2009-01-12
forum: General Help
---

### Post by horacle on 2009-01-12
how important is the .dbus folder backup wise? Im trying to backup with tar and when it reaches a file /root/.dbus/session-bus/a69111e9f2a28cf4c0f482fc49514dd0-0 it stops prematurely giving me an error message, in spanish :D can I just exclude it?


thanks

---

### Post by Titan8990 on 2009-01-12
anything is a home folder like that is user specific and typically safe to leave out.


curious, why tar? why not a real backup application such as rsync?

---

### Post by horacle on 2009-01-14
tar is easy? I need ot make a backup of some very critical data, the disk has being dieing form a couple of months now and I need to back it up soon and I dont know how, so Im looking for something easy an reliable. Somebody recommended me mondo, but testing it I found it very unreliable, so I decided to try with tar, I guess I could just try to make the backup from another machine in the lan with tar.

---

