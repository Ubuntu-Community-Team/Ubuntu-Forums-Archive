---
title: "wpa_supplicant"
date: 2005-11-08
forum: Desktop Environments
---

### Post by mosquitooth on 2005-11-08
Hi,

I just installed wpa_supplicant according to [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto), but unfortunately, the setup fails when I try to execute: 'sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw' as it prints just 'ioctl[SIOCSIWPMKSA]: operation not supported' to the screen.
(I'm using a centrino notebook with ipw2100, WPA-PSK (AES)).

Can anyone help?


-Peter

---

### Post by akseli on 2005-11-08
[QUOTE=mosquitooth]Hi,

I just installed wpa_supplicant according to [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto), but unfortunately, the setup fails when I try to execute: 'sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw' as it prints just 'ioctl[SIOCSIWPMKSA]: operation not supported' to the screen.
(I'm using a centrino notebook with ipw2100, WPA-PSK (AES)).

Can anyone help?


-Peter[/QUOTE]
Hey, this may be something that you've already checked and this may be an utterly useless post, but I was just thinking ... are you sure that your wireless connection is mapped to eth1? Personally since I'm running a RaLink chipset I have wireless as ra0 but that depends on the chipset. If I happen to be right you can find the real mapping in either your interfaces file or in the network manager.

Good luck...

---

### Post by mosquitooth on 2005-11-08
Yes, first thing I checked:)

---

