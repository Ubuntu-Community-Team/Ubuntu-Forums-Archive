---
title: "[SOLVED] Mount --Bind in fstab?"
date: 2008-11-11
forum: Desktop Environments
---

### Post by cantdrive55 on 2008-11-11
I am trying to get it so that I can automatically mount /media/windows/Documents and Settings/jclifford/My Documents and bind it to /home/jclifford/Documents. I had it setup in my previous install of hardy but I did a clean install of 8.10 today and am stuck on getting it configured again.

I have tried using ```
/media/windows/Documents\ and\ Settings\jclifford\My\ Documents /home/jclifford/Documents ntfs-3g rw,bind 0 0
``` but that doesnt work. 

I have it setup so that /media/windows mounts automatically at boot already in fstab.

---

### Post by cantdrive55 on 2008-11-12
Nevermind, I figured it out.

```
/media/windows/Documents\040and\040Settings/Jeff/My\040Documents /home/jclifford/Documents none bind 0 0
```

Found:
[http://ubuntuforums.org/showpost.php?p=1266239&postcount=4]("http://ubuntuforums.org/showpost.php?p=1266239&postcount=4")

---

### Post by blackened on 2008-11-12
You can also just surround the string with quotes and it should work to accomodate the spaces.

---

### Post by Denestria on 2008-11-12
> **blackened said:**
> You can also just surround the string with quotes and it should work to accomodate the spaces.

You can't do that in fstab.  You escape the space with \ then use ascii code for a space like Can't did in the second post.  **\040**

---

### Post by blackened on 2008-11-12
> **Denestria said:**
> You can't do that in fstab.  You escape the space with \ then use ascii code for a space like Can't did in the second post.  **\040**

Oh right. I was thinking of mount.

---

