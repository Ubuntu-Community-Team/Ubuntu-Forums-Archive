---
title: "unmount"
date: 2009-05-27
forum: General Help
---

### Post by Willy3 on 2009-05-27
Ubuntu 9.04 with Vista laptop. Attempted to set up sharing between the two then decided to undo but cannot unmount /media/RECOVERY. Get the following errors (screenshot).

---

### Post by albinootje on 2009-05-27
> **Willy3 said:**
> cannot unmount /media/RECOVERY. 

Try :
```

sudo umount /media/RECOVERY

```

---

### Post by SuperSonic4 on 2009-05-27
Open a terminal: System -> Accessories -> Terminal and paste the following command (shift+insert pastes in terminal)

```
sudo umount /dev/sda2
```

Alternatively you can launch nautilus as root by pressing alt+f2 and pasting the following command

```
gksu nautilus
```

Both will prompt you for your password but the first one in terminal won't show you typing but it is recognising them.

---

