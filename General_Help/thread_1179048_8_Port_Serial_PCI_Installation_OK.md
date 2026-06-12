---
title: "8 Port Serial PCI Installation OK"
date: 2009-06-05
forum: General Help
---

### Post by link194 on 2009-06-05
hi...i have 8 port pci serial card ......anyhow i mange to install the pci card ...

i  edit 
sudo nano /boot/grub/menu.lst

kopt=root=UUID=61070778-d126-4faa-a1e1-26b189e82f83 ro 8250.nr_uarts=8

after i boot the machine .....

dmesg |grep ttyS*

ports are there but ..if i plug a device on ttyS1 i have no communication...

setserial all  ready i install .....need to be change same think ????? to enable to communicate ttyS1 or other com ports...

can anybody help pls...thx

---

