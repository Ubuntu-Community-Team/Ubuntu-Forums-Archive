---
title: "sabayon-apply crashes"
date: 2007-11-18
forum: Desktop Environments
---

### Post by christian.paratschek on 2007-11-18
Hi!

I want to deploy Gnome Desktops in kiosk mode. Therefore I installed sabayon and created a user profile for a kiosk user with it.

But when I want to apply my profile, the script sabayon-apply crashes with the following errors:

> Es konnte kein Profil für Benutzer »root« gefunden werden
===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2007/11/18 11:06:55.1664 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2007/11/18 11:06:55.1668 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 106, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2007/11/18 11:06:55.1664 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2007/11/18 11:06:55.1668 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 106, in <module>
    sys.exit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000


The same happens on Fedora 8, so I guess it's a problem with sabayon. Is there any solution for this problem? I tried the XFCE kiosk mode but I am not very comfortablw with it. Gnome would be my preferred choice.

Regards,
Christian

I really want to deploy these Linux

---

