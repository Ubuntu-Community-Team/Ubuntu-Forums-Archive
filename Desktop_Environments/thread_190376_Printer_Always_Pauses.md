---
title: "Printer Always Pauses"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Ubuntist on 2006-06-06
I've just upgraded to Dapper from Breezy.  Under Breezy my Lexmark Z55 printer worked OK, and it still works perfectly when I boot to XP.  Under Dapper, however, the printer always pauses.  When I right-click the printer icon in the system tray, it unpauses but soon pauses again.  I can't print anything.

I don't know if its relevant, but the last line of /var/log/cups/error_log is
```
E [06/Jun/2006:11:47:16 +0100] cupsdAuthorize: Local authentication certificate not found!

```

I've looked at other threads regarding printer pauses, but they seem either specific to other kinds of printers or are closed.

Any hints would be appreciated!

---

### Post by Ubuntist on 2006-06-06
I eventually solved the problem by going to System -> Administration -> Printing
and deleting the printer and then re-installing it.

---

