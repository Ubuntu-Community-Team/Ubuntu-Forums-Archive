---
title: "I accidentally deleted /etc/group"
date: 2009-01-30
forum: General Help
---

### Post by Noo on 2009-01-30
I accidentally deleted /etc/group. I do have a backup but I can't sudo anymore to put it back. Any ideas? I'm afraid to reboot because it might mess up my entire system.

---

### Post by lykwydchykyn on 2009-01-30
If you break sudo, about all you can do is reboot to recovery mode so you can get a root shell.  Then recreate your group file from backup.

---

### Post by Noo on 2009-01-30
It worked, thanks!

---

