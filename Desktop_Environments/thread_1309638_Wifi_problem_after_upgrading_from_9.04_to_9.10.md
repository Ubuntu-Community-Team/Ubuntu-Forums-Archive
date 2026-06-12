---
title: "Wifi problem after upgrading from 9.04 to 9.10"
date: 2009-11-01
forum: Desktop Environments
---

### Post by n00binberg on 2009-11-01
First off, I'm a total n00b as my handle suggests. Not sure what happened but, my wifi adapter worked in 9.04. After the upgrade to 9.10 restart I suddenly have no wifi. My adapter is Alfa Network USB AWUS036H. It doesn't seem normal for an upgrade to uninstall drivers for working hardware, to me anyway. I'm assuming that during the upgrade it turned it off or switched my default connection or something. I really don't know. Wifi is the only means for internet on that box so, I need to get it working (XP sucks but, at least I can install the drivers for the adapter and get online.)
 
I ran some things that might give you the info you will need to help me. 
 
 
 
buntuser@ubuntu:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry long limit:7 RTS thr::ooff Fragment thr::ooff
Power Management::ooff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
 
 
buntuser@ubuntu:~$ ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:19 errors:0 dropped:0 overruns:0 frame:0
TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:1100 (1.1 KB) TX bytes:1100 (1.1 KB)
 
 
 
buntuser@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by n00binberg on 2009-11-01
Weird thing that happened. I thought I might try to boot into the other kernal option (not sure what the kernal was but, it had a lower number.) When I got into the OS I had internet for about 3 minutes then it went away...seemed pretty odd.

---

### Post by aimaaditya on 2009-11-02
i had the problem after fresh install of 9.10.

insert the cd again, enable cd as source in software sources....

run update,

go to system, administration, harware drivers...

it must reinstall the drivers

---

