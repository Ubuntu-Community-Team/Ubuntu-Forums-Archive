---
title: "SOS Crashed during upgrade, need help reloading"
date: 2010-09-01
forum: Desktop Environments
---

### Post by GMcNulty on 2010-09-01
Help! My laptop crashed in the middle of upgrading from Hardy Heron to 10.04. Now I can't boot at all. It'll load grub and let me pick an older kernal which gives me a reasonably familiar shell or I can let it go to the latest and it gives me some strange shell with very limited commands. Anyone have any idea how to proceed from here? 
 
Thanks in advance.

---

### Post by arrange on 2010-09-01
I would boot into a LiveCD, back up all important data from the Ubuntu partition (or, alternatively, back up all */home*), and do a clean install.

---

### Post by GMcNulty on 2010-09-04
K, I'll try that. Waiting for a iso that a friend made for me. Should be here in the mail today. Not sure if I can back anything up, though. As it now stands, when I try to mount my external drive it returns 'cannot create directory `/Media/NewVolume': Read-only file system. When I list it, though, it shows permissions for /media/ as drwxr-xr-x :-k

---

### Post by arrange on 2010-09-04
You will be able to from the LiveCD. If not, paste the error message here, and possibly the output of```
dmesg | tail -20
```

---

