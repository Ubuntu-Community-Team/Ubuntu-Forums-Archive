---
title: "Compiz Not Working Anymore"
date: 2009-02-08
forum: General Help
---

### Post by GuitarFreak1857 on 2009-02-08
I updated my system a couple weeks ago and when i rebooted all my eye candy was gone. It is all selected in the advanced desktop effects settings, like wobbly windows or rain but no toggles work and everything looks very plain. I reinstalled my video drivers, reinstalled compiz, and it still doesn't work. I'm running Xubuntu 8.04 xfce btw. Any advice would be great.  In the other forum i go to they asked me to go to visual effects window but i cannot find that in xubuntu and i can't find anything on how to get there. 

~thanks

---

### Post by gettinoriginal on 2009-02-08
Try in terminal:
```
compiz --replace
```

---

### Post by GuitarFreak1857 on 2009-02-08
administrator@linux-laptop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting
administrator@linux-laptop:~$ 

no driver found?

---

### Post by gettinoriginal on 2009-02-09
I do not know the layout of xfce, but you need to go to settings and find Hardware Drivers and enable it.  Sometimes updates will disable it during the update.

---

