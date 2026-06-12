---
title: "Inspiron 17R 5720 - No drivers available"
date: 2012-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NilPointer on 2012-10-16
I've installed Linux Mint 13 instead of Ubuntu 11.10 on my Inspiron 17R 5720, but there is no 3rd-party drivers available (on 11.10 there were Wi-Fi, Bluetooth and Touchpad). Since Mint 13 is based on Ubuntu 12.04, there probably will be no drivers either on 12.04? So, is there a way to get Dell drivers for Mint 13 (perhaps there is Dell PPA)?

---

### Post by NilPointer on 2012-10-20
I've installed Ubuntu 12.04 LTS back and managed to install touchpad driver (found it on backup drive I made for 11.10). Now I don't really care about bluetooth, but what to do with WLAN? Since original 11.10 listed Broadcom STA driver for Wi-Fi, I guess I have to get it for 12.04 too. I found some instructions for installing it via module-assistant and tried:

```
sudo m-a a-i broadcom-sta
```

But building fails. How to get Wi-Fi running?

Ah, yes. And in lspci, Wi-Fi module appears to be Broadcom Corporation Device 4365 (rev 01)

---

### Post by NilPointer on 2012-10-21
Looks like I've reached end of that long maze on my own. I've installed modified deb from here:

[https://www.dropbox.com/s/jerkl6uqal5ylv3/wireless-bcm43142-dkms-6.20.55.19_amd64.deb](https://www.dropbox.com/s/jerkl6uqal5ylv3/wireless-bcm43142-dkms-6.20.55.19_amd64.deb)

And loaded kernel module "wl". After that, Wi-Fi started to work. I added wl to autoload at boot time... Anyway, looks like problem is solved.

---

