---
title: "tethering on ubuntu"
date: 2011-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by argoz17 on 2011-03-09
Hello, I have a Dell Dimension 4300 and its OS is Ubuntu 10.10, I have no internet on it...currently the only web options at my home are tethering from a AT&T blackberry. How can I usb tether with this phone and get internet on my Dell running Ubuntu? I use the Bluetooth tethering option on it for my mac, but the dell only has a usb option.

---

### Post by dcommini on 2011-04-17
bump

---

### Post by 3togo on 2011-05-23
Try unmanaged the NetworkManager, it works for me


[3togo:~]$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

---

