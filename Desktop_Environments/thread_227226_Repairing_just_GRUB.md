---
title: "Repairing just GRUB?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by gurgle on 2006-08-01
I need to reinstall Windows, and after I do that GRUB will not be loaded. I would like to keep my Ubuntu install intact, can i just reinstall GRUB from the LiveCD?

---

### Post by Ramses de Norre on 2006-08-01
Yes, do 
```
sudo grub
root (hd0,0)
setup (hd0)
quit
```
After "root" you define the device and partition containing /boot/, it starts counting form 0. After "setup" you define where grub is to be installed, (hd0) is the mbr.

---

