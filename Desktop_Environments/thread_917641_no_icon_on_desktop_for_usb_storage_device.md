---
title: "no icon on desktop for usb storage device"
date: 2008-09-12
forum: Desktop Environments
---

### Post by b-boy on 2008-09-12
Hi guys 

The problem i am having is when i plug a usb storage device like a memory stick or an external hard drive it does not show an icon on the desktop (like it use to)the icon only appear under places

---

### Post by b-boy on 2008-09-12
problem solved after deleting file
 

```
sudo rm /etc/hal/fdi/policy/gparted-disable-automount.fdi 
```

---

### Post by amr2205 on 2008-09-21
> **b-boy said:**
> problem solved after deleting file
 

```
sudo rm /etc/hal/fdi/policy/gparted-disable-automount.fdi 
```

Well, it works for me too, I hope it doesn't affect Gparted :biggrin:

---

