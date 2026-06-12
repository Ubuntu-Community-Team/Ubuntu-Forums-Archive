---
title: "Gparted error"
date: 2009-04-23
forum: General Help
---

### Post by zero777zero on 2009-04-23
hello i just installed 9.04 64bit. i then installed GParted and i tried to open it only to get this error:

Failed to run /usr/sbin/gparted as user root.

Unable to copy the user's Xauthorization file.

---

### Post by riseringseeker on 2009-04-23
> **zero777zero said:**
> hello i just installed 9.04 64bit. i then installed GParted and i tried to open it only to get this error:

Failed to run /usr/sbin/gparted as user root.

Unable to copy the user's Xauthorization file.

I would guess you did not run it as root.  Were you running it from the command line?  If so, put "sudo " in front of the command and try again.

---

### Post by oldos2er on 2009-04-23
> **zero777zero said:**
> hello i just installed 9.04 64bit. i then installed GParted and i tried to open it only to get this error:

Failed to run /usr/sbin/gparted as user root.

Unable to copy the user's Xauthorization file.

 ```
gksu gparted
```

---

### Post by zero777zero on 2009-04-23
hi i just reinstalled jaunty due to a dual boot config error and this problem was gone after reinstallation.

in case the info is useful, i installed it via add/remove without touching the command line and tried to launch from the ubuntu menu.

---

