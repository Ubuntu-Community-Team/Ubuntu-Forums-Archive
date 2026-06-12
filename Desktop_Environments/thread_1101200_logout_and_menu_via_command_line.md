---
title: "logout and menu via command line"
date: 2009-03-20
forum: Desktop Environments
---

### Post by ororo on 2009-03-20
I would like to perform each one of the following operations from command line (e.g. konsole):
(i) close the KDE session
(ii) pop-up the main K menu
(iii) pop-up the "Logout/Shutdown/Reboot" dialog.

Is there anybody able? Thank you!

---

### Post by Aikanar on 2010-02-09
I know that this is almost a year later, but for (iii), the command is:

```
qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout 1 -1 -1
```

Tested and working on KDE 4.3.4 (sidux).  I use this with xbindkeys to assign it to my keyboard's Sleep/Logout key.

///Dave

---

