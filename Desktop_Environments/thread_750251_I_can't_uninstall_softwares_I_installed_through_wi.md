---
title: "I can't uninstall softwares I installed through wine"
date: 2008-04-09
forum: Desktop Environments
---

### Post by amlife on 2008-04-09
Hello all 

I have used this command through command prompt 

```
wine uninstaller
``` 

fine .. I like GUI .. I removed bunch or crap I installed . .I have problem removing safari browser and apple update manger .. 

is there is anything to force removal ?

Thanks

---

### Post by warp99 on 2008-04-10
> **amlife said:**
> Hello all 

I have used this command through command prompt 

```
wine uninstaller
``` 

fine .. I like GUI .. I removed bunch or crap I installed . .I have problem removing safari browser and apple update manger .. 

is there is anything to force removal ?

Thanks

Sure, all of the software is installed locally in your '/home/$user/.wine' directory. Now that directory is a hidden directory, so make sure you turn on view hidden directories in Nautilus. If you delete the entire directory the next time you start wine it will create a new one, but any other software you installed will also be removed. You also need to remove entries in these directories:

```
/home/$user/.local/share/applications/wine/Programs
```
and
```
/home/$user/.local/share/desktop-directories/
```

these are also hidden directories. Hope this helps.

---

