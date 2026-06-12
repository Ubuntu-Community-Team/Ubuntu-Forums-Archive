---
title: "changing permissions for folders and subfolders"
date: 2005-10-02
forum: Desktop Environments
---

### Post by Psquared on 2005-10-02
I played around with zeroinstall Rox-Session and now I am trying to remove all vestiges from my machine. that sucker has taken up residence in every file. Mainly in the /var folder. Lots of sub-folders with lots of files none of which I have the right permissions. I have to locate the file using terminal and sudo rm and then sudo rmdir. It is taking forever. Surely there is a faster way.

Can I start Nautilus with SU permission so I can just delete them? Will they just take up residence in my trash can and I'll have to do it all over again?

---

### Post by aysiu on 2005-10-02
[QUOTE=Psquared]
Can I start Nautilus with SU permission so I can just delete them?[/QUOTE] Yes, just type ```
gksudo nautilus
```

---

