---
title: "KDE / X randomly crashes."
date: 2010-04-16
forum: Desktop Environments
---

### Post by jpmallory on 2010-04-16
My PC has been experiencing intermittent crashes of X server for some time now.  Sometimes it will run for a week without a problem, and other days, (like this morning) it will crash multiple times.

By crash, I mean that the screen flickers for a second and the X server dies. (I usually swear loudly at around this point). Then X relaunches itself and I'm greeted with the login screen.

Here's all I could find in the syslog:
Apr 16 10:16:08 jmallory-ws kdm[1804]: X server for display :0 terminated unexpectedly
Apr 16 10:16:08 jmallory-ws acpid: client 13788[0:0] has disconnected
Apr 16 10:16:08 jmallory-ws acpid: client 13788[0:0] has disconnected

I'd love to find a resolution to this issue.  Please let me know what additional information will be relevant to troubleshooting this.

Thanks

---

### Post by micio on 2010-04-16
Try to add NOACPI to boot line in bootloader option or try to disable the acpi service.

---

### Post by jpmallory on 2010-04-21
I tried the noacpi suggestion, and the result was that the system locked up hard after 10-15 minutes of use.  This happened twice, so I've changed it back.

---

### Post by Zorael on 2010-04-21
Check **/var/log/Xorg.0.log** and **/var/log/kdm.log**, too. Note that Xorg.0.log gets incremented when X restarts, so refer to **Xorg.0.log.old** for the last session's log. kdm.log just gets appended.

---

