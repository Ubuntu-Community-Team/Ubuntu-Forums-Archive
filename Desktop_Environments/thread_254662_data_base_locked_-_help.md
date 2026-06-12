---
title: "data base locked - help"
date: 2006-09-10
forum: Desktop Environments
---

### Post by guest5 on 2006-09-10
this is the message:

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.


this is what happened:

i was installing java runtime for mozilla, 5.0,6 i believe, but the package manager locked up at 23%, so after an hour or so i closed it.

ouch.

ps, rebooting did not help.

---

### Post by guest5 on 2006-09-10
i got it.  i decided to goto the console and run install to see if i got any messages that might help, and i did:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


this cleared things up and freed the data base for me, allowing me access, but while i was in console i went ahead and installed from console mode.  i like the console.

---

