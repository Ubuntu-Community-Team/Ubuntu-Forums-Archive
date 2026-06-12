---
title: "sudo help"
date: 2006-07-30
forum: Desktop Environments
---

### Post by pkryan on 2006-07-30
whenever i try to run a sudo command i get[PHP]sudo: /etc/sudoers is mode 0755, should be 0440[/PHP]
How can i fix this?

---

### Post by Paerez on 2006-07-30
reboot and choose the "recovery" mode in grub. Then when you get the command prompt, type:
```
chmod 0440 /etc/sudoers
```

edit: after that type "reboot" to reboot.

---

