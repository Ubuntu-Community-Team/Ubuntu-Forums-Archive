---
title: "Unnecessary modules"
date: 2006-01-09
forum: Desktop Environments
---

### Post by djjazzyjeff on 2006-01-09
I have a question about what loads at startup. As I watch my machine start, I see things that I wonder whether I need. Looking at dmesg output, things such as:

[4294734.428000] Bluetooth: Core ver 2.7
[4294734.428000] Bluetooth: HCI device and connection manager initialized
[4294734.428000] Bluetooth: HCI socket layer initialized
[4294734.485000] Bluetooth: L2CAP ver 2.7
[4294734.485000] Bluetooth: L2CAP socket layer initialized
[4294734.527000] Bluetooth: RFCOMM ver 1.5
[4294734.527000] Bluetooth: RFCOMM socket layer initialized
[4294734.527000] Bluetooth: RFCOMM TTY layer initialized 

no Bluetooth on my Latitude C640 notebook

loads related to LVM and RAID, also not on my C640.

How to I remove this unnecessary stuff fro loading at boot time? Thanks......Jeff

---

