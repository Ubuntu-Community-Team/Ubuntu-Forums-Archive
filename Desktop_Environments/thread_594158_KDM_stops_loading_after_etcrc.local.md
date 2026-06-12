---
title: "KDM stops loading after /etc/rc.local"
date: 2007-10-27
forum: Desktop Environments
---

### Post by limplenny on 2007-10-27
when i rebooted for the first time after changing some packages, 
(where the only ones i can think might have caused the errors are: the removal of nvidia-glx-new (or whats it called?) and installed nvidia-glx)

when kdm starts loading, right after rc.local script has loaded (it says [OK], nothing in rc.local except: exit 0) it stops and nothing else happens. I have no clue what's loaded after rc.local so i don't know what the problem might be. I changed xorg.conf back to my first backup, and that didn't help.

I tried solving it myself and i did the following:
```
sudo apt-get remove --purge kdm
sudo apt-get install kdm kubuntu-desktop
```

but again the same error reoccured.

any thoughts? thanks in advance
lennard

---

