---
title: "Strange Networking Problem"
date: 2005-12-05
forum: Desktop Environments
---

### Post by adas108 on 2005-12-05
I am new user of Ubuntu and I really like it!!! But I have some issues with the networking and I hope somebody can help me. I have a toshiba satellite M45-S355 laptop which has a mavell yukon network card and intel pro wireless 2200BG wireless card. When I stalled ubuntu for first time the marvell yukon network card is not detected and I think I can take care of the installation of the driver later once my internet starts working but the strange part is the wireless starts working for the first time. I can access the internet fine but when I reboot then at the time of "Configuring network Interfaces" it gets stuck up and the problem starts from there and as soon as I login the the wireless connection is gone. nothing working...I can't even ping my router. It has happened to me twice. I don't want to install ubuntu so many times. Please HELP!!! I have been working on it for a while!!! so any help is appreciated. thanks...

---

### Post by 23meg on 2005-12-05
Make sure your wireless adapter is configured, activated and selected as the default gateway in System / Administration / Networking .

---

### Post by adas108 on 2005-12-05
23Meg...
thanks for quick response!!! Everything you have asked is done. thats why I said its very strange that it works for the first time and after reboot its gone!!! Please tell me if you think anything else can be wrong!!! thanks again

---

### Post by 23meg on 2005-12-05
Maybe it's a DHCP problem; see if setting a static IP for it on your router and configuring for static ip in Networking works.

---

### Post by stozka on 2005-12-05
well, I was having same problems, when I install for real (live cd works without any problems ??), my network cards, LAN and Wi-fi were working and then again not,

real pain,

then I put this into my /etc/network/interfaces

iface lo inet loopback
iface eth0 inet dhcp
iface ath0 inet dhcp
wireless-essid untitled

auto eth0
auto ath0
auto lo

if I forget very slow boot, that's it. It works anytime.

untitled is name ssid name for your wifi.

---

