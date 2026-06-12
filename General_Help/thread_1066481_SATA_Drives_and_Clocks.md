---
title: "SATA Drives and Clocks"
date: 2009-02-10
forum: General Help
---

### Post by thegodfaza on 2009-02-10
I have two problems with my install of Intrepid Server 8.10.

The first is a little annoying. My software clock runs at 2x speed. When I resync to the system clock it is correct again.

The second is more important. I can't get Ubuntu to see my SATA drive. Windows saw it just fine in every machine including the one that Ubuntu is on. But it won't show up. I tried using the pci=nomsi boot option but it has no effect. Ubuntu can see the SATA controller.
```
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379]
```
As you can see the mobo is an ATI chipset but the SATA controller is VIA based.

Any help is appreciated.

---

### Post by thegodfaza on 2009-02-11
[ bump ]

---

