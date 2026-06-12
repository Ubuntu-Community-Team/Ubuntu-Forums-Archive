---
title: "delete programs"
date: 2009-02-24
forum: General Help
---

### Post by esteel75 on 2009-02-24
hi all,
i dont know how to uninstall/delete programs that have been down loaded.
only ones that i can do are the ones in the general add/remove file but things downloaded elsewhere i havent a clue what to do
any info appreciated
eleanor

---

### Post by howefield on 2009-02-24
Synaptic will keep track of your downloaded programs even if you haven't installed them via synaptic.

Load up synaptic and select the Origin button, then local/main will show what you have downloaded and installed outside of synaptic.

---

### Post by todak on 2009-02-24
In a terminal ```
sudo apt-get remove <program-you-want-to-remove>
``` will remove it.

---

### Post by heindsight on 2009-02-24
> **howefield said:**
> Synaptic will keep track of your downloaded programs even if you haven't installed them via synaptic.

Load up synaptic and select the Origin button, then local/main will show what you have downloaded and installed outside of synaptic.

> **todak said:**
> In a terminal ```
sudo apt-get remove <program-you-want-to-remove>
``` will remove it.

Both those assume that you installed using a .deb package. There are many ways of installing things and each has it's own methods for uninstalling (in some extreme cases the only way to uninstall is to manually hunt down and delete each installed file). If you did not install from .deb packages, you'll have to provide more information on what you installed and how.

---

