---
title: "HOWTO: completely remove &quot;wine&quot; and parts"
date: 2011-06-27
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-06-27
I installed WINE onto my Ubuntu Lucid v10.04 LTS workstation. Now I want to remove it completely.  

When I use Synaptic, it tells me that Wine is not installed.  However, when I select **Applications** from the top panel, **Wine** appears as the top-most entry and **Wine --> Programs** has contents.

[highlight]How do I make Wine EVERYTHING go away?[/highlight]

Merci d'avance,
~~~ 0;-Dan

---

### Post by 73ckn797 on 2011-06-27
In a terminal run:
```
 sudo apt-get purge wine
```

---

