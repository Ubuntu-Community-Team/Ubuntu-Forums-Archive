---
title: "usb mobile"
date: 2009-04-02
forum: General Help
---

### Post by vlada92 on 2009-04-02
hi there!
i wana ask 1 question.
i connected my mobile via usb, and it creates new icon "USB drive", but when i click on that icon, it shows one warning, that i have to mount that volume! can u tell me how to mount USB drive?!??

---

### Post by TyrantWave on 2009-04-02
There are two ways:

First, graphical:
Get the program "Mount Manager" from the Add/Remove programs. This will let you mount your USB manually.
Find your USB device, and right click -> mount

Second way is to open a terminal, and do:
```
sudo mount /media/*your usb device*
```

Although USB devices should auto-mount anyway...

---

