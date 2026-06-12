---
title: "Wirleless not connected in Ubutu 12.04"
date: 2014-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pmurugaraj on 2014-01-08
I have purchased a new Dell inspiron 15 3521 laptop. Initially both  wired LAN as well wirelsss in not working. After configuring the manual  IP address for LAn, wired network is working. Wireless is also working  for some time after upgrade and restart network-manager. Suddenly it is  not working. output of various commands are as follows. can someone help  me on this.
  Thanks in advance for your support....
  regards,
  Muru

Output of some of the commands are as follows
**lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:42:f0:ac
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.20 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 3c:77:e6:a0:4c:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-58-generic firmware=N/A ip=192.168.1.13 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0500000-c057ffff memory:afb00000-afb0ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
murugaraj@murugaraj-Inspiron-3521:~$** uname -a**
Linux murugaraj-Inspiron-3521 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
murugaraj@murugaraj-Inspiron-3521:~$ **lspci | grep -i wireless**
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
murugaraj@murugaraj-Inspiron-3521:~$** rfkill list all**
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by Bucky Ball on 2014-01-08
There is a solution at the bottom of post #1 here:

[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)

You could give that a shot.

---

