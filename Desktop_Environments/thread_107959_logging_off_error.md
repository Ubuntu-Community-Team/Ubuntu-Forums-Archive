---
title: "logging off error"
date: 2005-12-24
forum: Desktop Environments
---

### Post by nami on 2005-12-24
Hi

Each time I log off I get the following error which it starts to stop every thing:

/etc/rc6.d/K20clamav-freshclam: line 163: log_daemon_msg: command not found

anyone know how to fix this?

nami

---

### Post by dcstar on 2005-12-24
[QUOTE=nami]Hi

Each time I log off I get the following error which it starts to stop every thing:

/etc/rc6.d/K20clamav-freshclam: line 163: log_daemon_msg: command not found

anyone know how to fix this?

nami[/QUOTE]
Remove (including configuration files) ClamAV & Freshclam, and then re-install it (if you use it).

---

### Post by nami on 2005-12-25
That did the trick! Thanks.

---

