---
title: "i keep getting this error"
date: 2006-07-17
forum: Desktop Environments
---

### Post by ice.man on 2006-07-17
after i asked a mate to setup something i keep getting this error /etc/sudoers is mode 0777, should be 0440 how do i fix???

---

### Post by Lunar_Lamp on 2006-07-17
Well, I have never seen this before, so take what I say with a pinch of salt.  However:

"chmod 0440 /etc/sudoers" 

would seem to fix it.  You may need root access to do this.

---

### Post by ice.man on 2006-07-17
how do i get root access ???

---

### Post by lvleph on 2006-07-17
Try this in the terminal
"sudo chmod 0440 /etc/sudoers"

---

### Post by aysiu on 2006-07-17
> **ice.man said:**
> how do i get root access ???
Boot into recovery mode.

---

