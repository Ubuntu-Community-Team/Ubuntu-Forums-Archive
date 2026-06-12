---
title: "Wifi support on Dell Inspiron 1440"
date: 2010-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vinu Raj V on 2010-04-27
Hi, i'm using Ubuntu 9.10(32 bit) on my Dell Inspiron 1440 laptop. The wifi device is 'Dell™ Wireless 1397 802.11b/g Half Mini Card'. How can i get wireless support on my laptop.

Thanks in advance.

---

### Post by coffeeaddict22 on 2010-04-27
Hi,
The name you've given isn't quite enough info.  

One answer to your problem: go into System/Administration/Hardware Drivers and enable the Broadcom STA driver.

Another answer: have a look at the [Wifi troubleshooter]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") for some of the information you can get about your network interface.  In particular, your card information is best got off ```
lspci
``` or if you want more info, ```
lshw -C network
```.

---

### Post by Telescope_Nerd on 2010-04-27
Hi Vinu
I had a bit of trouble getting wifi working on my dell laptop on 9.10 this was largely down to the kernel module called "dell-laptop" you can temporarily disable this module by doing

```
sudo rmmod dell-laptop
```

try that and see if it gets wifi working.
T

---

### Post by rha7dotcom on 2010-07-12
> **Telescope_Nerd said:**
> Hi Vinu
I had a bit of trouble getting wifi working on my dell laptop on 9.10 this was largely down to the kernel module called "dell-laptop" you can temporarily disable this module by doing

```
sudo rmmod dell-laptop
```

try that and see if it gets wifi working.
T

Full instructions would be to go to a terminal and type the above command, then go to System -> Administration -> Hardware Drivers, and then on that Window, install the Broadcomm STA driver, you will need to connect a physical network cable to be able to install them. Afterwards, you will need to reboot. Do so, also you can disconnect your ethernet network cable now. Configure your wifi now, and enjoy.

Greetings,

Gabriel Medina.

---

