---
title: "CDRom and USB removable drives problem"
date: 2005-05-06
forum: Desktop Environments
---

### Post by carlisg on 2005-05-06
Hi

Every time I plug an external USB drive or insert a CD in the CD-ROM unit it gets automatically mounted and a new icon shows in the desktop. Anyway none of them is mounted as utf8, and I need it to be so. I wonder if there some way of doing that graphically (like an option in the preferences menu or through some app).
If not I would appreciate some help here cause I have no idea where to start.

Apart from that, my CD has DMA transfer mode disabled, I have tried using hdparm -d1 /dev/cdrom and it seems to work, but I lose this configuration every time I reboot. Is there any file or place where I can set DMA transfer on permanently?

Thanks.

---

### Post by enquiry on 2005-05-06
[QUOTE=carlisg]
Apart from that, my CD has DMA transfer mode disabled, I have tried using hdparm -d1 /dev/cdrom and it seems to work, but I lose this configuration every time I reboot. Is there any file or place where I can set DMA transfer on permanently?
[/QUOTE]
Yes, add these lines at the bottom of /etc/hdparm.conf:

/dev/dvd {
dma = on
}

---

