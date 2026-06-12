---
title: "Kate crashed, now it won't start at all"
date: 2005-04-30
forum: Desktop Environments
---

### Post by mortram on 2005-04-30
invoking Kate from the shell or the KDE Menu doesn't work.  I can only use the "preview in Advanced Text Editor" context-menu in conqueror...  Is there something I need to 'flush out' to get it running again?

---

### Post by WildTangent on 2005-05-01
kate doesnt work at all for me :( overall im not impressed with kubuntu at all. i dont seem to have my superuser priviledges, i cant edit anything at all

-Wild

---

### Post by tomchuk on 2005-05-01
Try:
```
rm -rf ~/.kde/share/apps/kate*
rm -rf ~/.kde/share/config/kate*
```

---

