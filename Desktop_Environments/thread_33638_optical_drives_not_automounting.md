---
title: "optical drives not automounting"
date: 2005-05-11
forum: Desktop Environments
---

### Post by mrt on 2005-05-11
After coming back from vacation, I booted Ubuntu only to find my optical (dvd and cdrw) drives no longer auto mount when I put a cd in them.  Also, I tried to burn some files from nautilus, but my cdrw drive was no longer listed; I could only burn to file.  I am able to manually mount the drives.

Why would this happen, and how should I go about fixing it?

My usb camera auto mounts fine.

Here is part of dmesg:
```
hdc: TDK CDRW5200B, ATAPI CD/DVD-ROM drive
hdd: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X DVD-ROM drive, 512kB Cache
```

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=mrt]After coming back from vacation, I booted Ubuntu only to find my optical (dvd and cdrw) drives no longer auto mount when I put a cd in them.  Also, I tried to burn some files from nautilus, but my cdrw drive was no longer listed; I could only burn to file.  I am able to manually mount the drives.

Why would this happen, and how should I go about fixing it?

My usb camera auto mounts fine.

Here is part of dmesg:
```
hdc: TDK CDRW5200B, ATAPI CD/DVD-ROM drive
hdd: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X DVD-ROM drive, 512kB Cache
```[/QUOTE]
 does 
sudo /etc/init.d/dbus-1 restart
help?

---

### Post by mrt on 2005-05-11
[QUOTE=Alexander Kirillov]does 
sudo /etc/init.d/dbus-1 restart
help?[/QUOTE]

Sadly, no.

---

