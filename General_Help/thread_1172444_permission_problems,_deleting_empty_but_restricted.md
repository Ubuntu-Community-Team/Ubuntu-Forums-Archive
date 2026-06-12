---
title: "permission problems, deleting empty but restricted files"
date: 2009-05-28
forum: General Help
---

### Post by IbeeFreak705 on 2009-05-28
Hi.  I have 9.04, and have been trying to learn my way under the hood of Ubuntu.  One of the exercises had me create a profile, but after removing it, there is stil a residual file.  Today, I decided to download a directory for media codecs (medibuntu) but in the process of doing it via the Terminal, I created a bum file thanks to a typo.  Because of this, Synaptic Package Manager and Add/Remove programs will not load.  When I try to update via the Terminal, I get this: E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/mediubuntu.list .  I went into the directory manually via the GUI, but I cannot delete it.  How do I fix this problem?[SIZE=-1][COLOR=#009900]
            [/COLOR][/SIZE]

---

### Post by Dngrsone on 2009-05-28
Open up a terminal and enter:

```
gksudo nautilus
```

Hit Return (Enter key) and it should prompt you for your password, and then you should get a GUI file browser that will let you delete the offending file.

Be careful, though-- don't delete something important that will crash your system.

---

### Post by IbeeFreak705 on 2009-05-28
Thanks!  I stopped at the one file that hung up my updates because the other mentioned folders are so small.

Thanks!

---

### Post by Dngrsone on 2009-05-28
So, your update works now?

---

