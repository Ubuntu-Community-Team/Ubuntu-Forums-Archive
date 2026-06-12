---
title: "ubuntu 8.10 on vostro 1200"
date: 2009-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abduhu on 2009-07-28
I am new linux user and firstly use ubuntu. I tried to install ubuntu 9.04 on my dell vostro 1200 laptop but the wireless (intel pro wireless 3945 ABG) failed to work. It was disable. Then I tried to install ubuntu 8.10 on it and wireless showed enabled but it still failed to work and so did the soundcard.

I'd like to get a brief step by step guide to solve these problems for the beginner as me.

Thank you

---

### Post by philcamlin on 2009-07-28
what wireless card is in your laptop? we need to know that :D

try 

iwconfig

do you see anything ?

im heading off to work now ill try and help you after :)

---

### Post by abduhu on 2009-07-28
ok. here they are.

abduh@abduh-vostro1200:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

abduh@abduh-vostro1200:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: **Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)**
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)

thx b4.

---

### Post by superprash2003 on 2009-07-28
post output of
1)lshw -C network
2)sudo iwlist scanning

---

### Post by abduhu on 2009-07-28
here they are

abduh@abduh-vostro1200:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:9b:78:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1c:23:59:17:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.254.1 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:6f:de:70:b6:34
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


abduh@abduh-vostro1200:~$ sudo iwlist scanning
[sudo] password for abduh: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.


[SIZE=3]thx b4[/SIZE]

---

### Post by superprash2003 on 2009-07-29
i have a feeling your wifi card is switched OFF.. most laptops have a wireless switch or a key combination to make wifi ON..

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by abduhu on 2009-07-30
You are right. but there is only hot key (Fn+F2) on dell vostro 1200 keyboard and there no other physical switch to make wireless device on.

???

---

### Post by superprash2003 on 2009-07-30
so the hot key doesnt work?

---

### Post by abduhu on 2009-07-30
Yes. It doesn't work. I have tried also to set the keyboard layout to dell manufacturer but it still doesn't work. How to solve?

---

### Post by abduhu on 2009-08-03
Hi bro! Is there nothing to share seriously????

---

### Post by win4t4 on 2009-10-16
The physical switch is the wireless led near "vostro 1200". Just touch it

I hope it's not to late

---

