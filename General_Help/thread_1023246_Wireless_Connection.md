---
title: "Wireless Connection"
date: 2008-12-27
forum: General Help
---

### Post by millerst on 2008-12-27
Hi, I have a dell computer running Vista and I want Linux but when I put in the Live CD the wireless internet connection will not work. Can someone explain how to set up a wireless connection using Ubuntu?

Thanks
Stefan

---

### Post by pytheas22 on 2008-12-27
First of all, go to System>Administration>Hardware Drivers.  There may be an option there to enable your wireless card.  Please check.

If not, please go to Applications>Accessories>Terminal, run the following commands and post the output here:
```

lspci -nn
lsusb
lshw -C Network
sudo iwlist scan
uname -rm
```

With that information we can tell you how to install wireless drivers for your card.  If you want to practice getting it set up on the live CD before you actually install Ubuntu to the hard disk, that's fine too.

---

