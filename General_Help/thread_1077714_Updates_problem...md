---
title: "Updates problem.."
date: 2009-02-22
forum: General Help
---

### Post by Rodhill on 2009-02-22
I'm trying to install some updates but I can't because this notice shows this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 Can someone assist please and explain what I have to do.

Thank you

---

### Post by howefield on 2009-02-22
Open a terminal from the applications > accessories menu and type the following into it.

```
sudo dpkg --configure -a
```

Enter your password when asked and hit enter. (You won't see your password being entered)

---

### Post by Rodhill on 2009-02-23
Thanks, I tried that and this is what i got:-

rod@rod-desktop:~$ sudo dpkg --configure -a
[sudo] password for rod: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
rod@rod-desktop:~$ 


Any Ideas?

Rod

---

### Post by plucky on 2009-02-23
> **Rodhill said:**
> Thanks, I tried that and this is what i got:-

rod@rod-desktop:~$ sudo dpkg --configure -a
[sudo] password for rod: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
rod@rod-desktop:~$ 


Any Ideas?

Rod

This [link](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/) might help. Or search forums for **dependtry**

Good Luck

---

