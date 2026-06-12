---
title: "Please help me fix this error message"
date: 2009-02-01
forum: General Help
---

### Post by husky55 on 2009-02-01
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This error prevent me from using Synaptic Package Manager and Add/Remove functions.

I rebooted the system but the error remains.

Thank you for your help,

Updated: Fixed

---

### Post by The Cog on 2009-02-01
Open the terminal (Accessories->Terminal) and enter this command:
> sudo dpkg --configure -a
Should do the trick

---

### Post by gettinoriginal on 2009-02-01
usually when you get a "cache open" error, it means that more than one package manager is open (Synaptic, terminal, add/remove)  Make sure that when you are running ```
sudo dpkg --configure -a
``` that the terminal is all you have open.

---

### Post by husky55 on 2009-02-02
Thank you so much. That was exactly what happened.

---

