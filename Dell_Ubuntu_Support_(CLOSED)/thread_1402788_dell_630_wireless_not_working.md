---
title: "dell 630 wireless not working"
date: 2010-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ams15 on 2010-02-09
Hi,

Installed Ubuntu 9.10 on dell latitude 630. For some reason wireless is not activated. Any ideas are appreciated.

# depmod -a
# modprobe -l | grep wl
kernel/drivers/gpio/twl4030-gpio.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 

# ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

Thanks in advance.

---

### Post by PRC09 on 2010-02-09
Instructions for Broadcom cards.....



[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by PRC09 on 2010-02-09
The above post was an assumpution on my part that your Dell was using a Broadcom wireless card.To view network cards and wireless  use the following in the terminal  - sudo lshw -C network   This will tell you which cards you have.....

---

### Post by ams15 on 2010-02-10
:) Solved....the WIFI switch which is on the *left *of the Dell 630 was turned off, looked at BIOS at boot up and it controls bluetooth and WIFI. Turned it on, and things worked.

It uses Intel Wireless btw:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:23:94:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.12 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:fe8ff000-fe8fffff

---

