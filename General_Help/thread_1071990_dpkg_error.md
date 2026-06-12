---
title: "dpkg error"
date: 2009-02-16
forum: General Help
---

### Post by sansa dude on 2009-02-16
im kinda new to Ubuntu and while trying to install some programs i started getting a error message when ever i try to install programs from the add/remove list and when i go into the synaptic package manager i also get told that there is already an installer working when i try to install files from the .deb file format. 

the error message i get is:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

any sugestions on whats wrong? ive tried rebooting and closing all the open programs and nothings working. thanks in advance!

---

### Post by overlord.gaurav on 2009-02-16
Open a Terminal and do:
```
sudo dpkg --configure -a
```

---

### Post by sansa dude on 2009-02-16
> **overlord.gaurav said:**
> Open a Terminal and do:
```
sudo dpkg --configure -a
```

i did trying to run that but i didn't have sudo in front but it seemed to work thanks!

---

