---
title: "All filesystems check error"
date: 2006-01-16
forum: General Help
---

### Post by PuNGS on 2006-01-16
When I boot up Ubuntu, the Checking all filesystems checks fails, but Ubuntu works normally.

How can I fix this thing?

---

### Post by lysis on 2006-01-16
have you modified your partitions without updating fstab?

---

### Post by PuNGS on 2006-01-16
I did nothing. The previous boot was complete successful, and then it happened. But Ubuntu still loads normally after this error.

---

### Post by dcstar on 2006-01-16
[QUOTE=PuNGS]When I boot up Ubuntu, the Checking all filesystems checks fails, but Ubuntu works normally.

How can I fix this thing?[/QUOTE]
Edit /etc/default/rcS to have:

FSCKFIX=yes

Then any errors found will be fixed automatically.


(Note to any Ubuntu developers, why isn't this set as default for us "normal" users, if there are any filesystem errors most people will have to run fsck and answer "Y" to all the "fix?" prompts anyway, so why not make this step as easy as possible for the "human" users this distro is supposed to be for??........ [/soapbox mode])

---

### Post by PuNGS on 2006-01-16
It worked perfectly. Thanks!

---

