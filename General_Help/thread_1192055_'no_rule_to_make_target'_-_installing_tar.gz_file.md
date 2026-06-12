---
title: "'no rule to make target' -??? installing tar.gz file"
date: 2009-06-19
forum: General Help
---

### Post by arnicainthemembrane on 2009-06-19
I'm trying to install an xmms skin installer which isn't in the repos. 

INSTALL instructions were to cd to the extracted directory, xmmsskininstaller , then 'make xmmsskininstaller'. 

I got:

make: *** No rule to make target `xmmsskininstaller'.  Stop.

---

### Post by mc4man on 2009-06-19
not that I think or know if you need this installer but do this.

cd to the extracted folder and go
```
 make ./xmms_skin_installer
```
you should see an output like this and find a binary created in the folder (xmms_skins_installer

> doug@doug-laptop:~/Desktop/test6/xmmsskininstaller$ make ./xmms_skin_installer
cc     xmms_skin_installer.c   -o xmms_skin_installer


---

