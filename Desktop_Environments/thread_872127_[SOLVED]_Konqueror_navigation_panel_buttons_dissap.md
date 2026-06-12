---
title: "[SOLVED] Konqueror navigation panel buttons dissapear"
date: 2008-07-27
forum: Desktop Environments
---

### Post by kioftes on 2008-07-27
Hi! I hope i am not double posting...i did some research and i couldn't find anyone treating the same issue, so...here is the case: recently i experienced the exact same problem as it was stated in 

[http://ubuntuforums.org/showthread.php?t=28834&highlight=konqueror+navigation+panel]("http://ubuntuforums.org/showthread.php?t=28834&highlight=konqueror+navigation+panel")

After launching konqueror from a terminal i noticed....

```
trying to create local folder /home/kioftes/.kde/share/apps/konqsidebartng/webbrowsing: Permission denied
cp: accessing `/home/kioftes/.kde/share/apps/konqsidebartng/webbrowsing/entries/': Permission denied
```

For some reason the directory /konqsidebartng was owned by root and was read-only. So, i opened konqueror as su

```
kdesudo konqueror
```

went to $HOME/.kde/share/apps right clicked on konqsidebartng, properties, and changed the ownership and the permissions. After that my navigation panel was back!

---

