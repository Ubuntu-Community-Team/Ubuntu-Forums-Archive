---
title: "how to format..........????"
date: 2009-05-20
forum: General Help
---

### Post by muctadir on 2009-05-20
in ubuntu how can i format removable disks like pen drive........????

---

### Post by Ceiber Boy on 2009-05-20
Use gparted from the package manager, the program is simple, just select what drive you want to format and get on with it! be carefull not to format your hardisk by mistake!

---

### Post by HermanAB on 2009-05-20
Plug device in.
Run dmesg and note device name e.g. /dev/sdX1
Run sudo mkfs.vfat /dev/sdX1

---

### Post by xavierp94 on 2009-05-20
You can format a usb drive by using Gparted as mentioned before. Just make sure you click on the correct drive to format. ;)

---

### Post by colau on 2009-05-20
> **HermanAB said:**
> Plug device in.
Run dmesg and note device name e.g. /dev/sdX1
Run sudo mkfs.vfat /dev/sdX1
This seems easier!

---

