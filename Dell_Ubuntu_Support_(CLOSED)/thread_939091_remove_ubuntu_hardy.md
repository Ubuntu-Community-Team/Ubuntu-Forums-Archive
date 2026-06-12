---
title: "remove ubuntu hardy"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hashi856 on 2008-10-05
How do I uninstall Ubuntu from my computer leaving only windows?

---

### Post by erickghint on 2008-10-05
Just format the partition that Linux is on through windows disk management. Then extend the volume to take up the new empty space.

---

### Post by anjilslaire on 2008-10-05
Remove the LInux partions as noted, then put the MBR back to Windows-only:

Boot your Windows CD and from a cmd prompt:
```

fixmbr
fixboot

```

---

