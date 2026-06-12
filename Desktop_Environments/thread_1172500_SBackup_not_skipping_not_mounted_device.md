---
title: "SBackup not skipping not mounted device"
date: 2009-05-28
forum: Desktop Environments
---

### Post by MarcoPolloII on 2009-05-28
Hi,

Had problems with SBAckup, after selecting the checkbox "Abort backup after destination directory does not exists" in the GUI nothing as promised happend. It had no effect on SBackup. However after editing the /etc/SBackup.conf and setting stop_if_no_target = 0 to stop_if_no_target = 1 SBackup starts aborting the backups.

Handy when the backup medium is a removable disk of any kind.

Regards,
Marco.

---

### Post by GhodMode on 2009-08-29
I'm experiencing the same problem.

---

