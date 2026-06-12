---
title: "can't find my wireless driver."
date: 2009-03-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hubcity on 2009-03-27
i have lost my wireless.  totally.  can't find the driver...  i'm still new to ubuntu, i've been trying to upgrade to hardy heron, but it keeps failing.  itll work for a week or so, then my internet connections keep breaking, then i start getting grub errors at the boot.  reloaded 8.04.1 a couple of times, but i really have no idea what i'm doing.  rebooted from the cd again today, without a hitch, but i have no intelpro wireless in the hardware drivers file, and no option to connect to a wireless connection....

i'm on an older laptop now, but its prone to overheat.

please help.

---

### Post by ugm6hr on 2009-03-28
Give detail from the wifi help? link below.

---

### Post by hubcity on 2009-03-28
i am now connected to the internet through a wireless connection provided by my landlord.  comcast. i found it was set wrong through system>admin>network...i had entered our network name earlier, and switched it to roaming mode, my mistake...  however, i continue to have issues with the connection.  it sometimes freezes or disconnects at random, for no apparent reason.  i know this because i have a gateway with windows that i've been operating at the same time(independently) and it is consistent.  instead of connecting automatically to "centralia perk", i always have to reenter the pass word and all the specifics 1/2 the time, and this is the frustrating part...lack of consistency.  it just happens some time...  i'm afraid the system is going to start doing what it has the last four times ive tried to operate ubuntu...works for a few days, then problems, then getting stuck at the boot with an automatic system check, back to bios (?) with a lengthy fschk, and ultimatelly, failure.  i wonder if this has something to do with my wireless driver, since that seems to be where the issues begin....

i've entered the info from your link below, hope you can help.

oh.  i'm a newbie, so the simpler the talk, the better.

thanks.    


trying to connect through wireless connection, comcast

Code:

lspci
lsusb
lshw -class network





 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
jim@jim-laptop:~$ lsusb
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:29:a5:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.107 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:76:b3:73
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes


i have ubuntu 8.04.01

code:
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 [www.opendns.com](www.opendns.com)

results in:

eth0      Link encap:Ethernet  HWaddr 00:19:b9:76:b3:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78600 (76.7 KB)  TX bytes:78600 (76.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:29:a5:34  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe29:a534/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4999933 (4.7 MB)  TX bytes:994071 (970.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-29-A5-34-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"centralia perk"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:66:46:FB:08   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=39/100  Signal level=-86 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@jim-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
jim@jim-laptop:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

jim@jim-laptop:~$ ping -c 3 [www.opendns.comPING](www.opendns.comPING) [www.opendns.com](www.opendns.com) (208.67.219.99) 56(84) bytes of data.
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=1 ttl=50 time=34.2 ms
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=2 ttl=50 time=38.2 ms
64 bytes from [www.opendns.com](www.opendns.com) (208.67.219.99): icmp_seq=3 ttl=50 time=38.9 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 34.233/37.122/38.928/2.070 ms
jim@jim-laptop:~$ 


windows is completely removed from my computer, when i loaded ubuntu, i opted for guided instalation using entire partition.

i'm not sure about the  encryptions or channels i'm using for wifi...

thanks, jim.

---

### Post by ugm6hr on 2009-03-28
Your problems sound like they have nothing to do with your wifi driver, which is working just fine.

The only potential wifi issue is the intermittent dropped connection, although I am still unconvinced.

I would suggest doing a hardware diagnostic on your HD and memory.

---

### Post by hubcity on 2009-03-28
is it possible i have some residual corruption from an earlier version  (i started with 7.10, went to hardy, tried intrepid {both online}, ended up back at 7.10 and to hardy again {with a cd}....) or my previous ms os?  i did a memory check from the boot menu, and that all turned out fine.

i'm just not sure what to look for to pinpoint my problem.  or where to look... i'm gradually learning how to work with ubuntu (it seems a lot like snowboarding.. i'm just waiting for the aha!)  is there an ubuntu system check or scan available to tell me if there are ant corruptions?

---

