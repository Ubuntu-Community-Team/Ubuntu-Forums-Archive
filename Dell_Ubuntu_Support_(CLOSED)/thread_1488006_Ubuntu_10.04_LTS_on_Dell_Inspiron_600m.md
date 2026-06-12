---
title: "Ubuntu 10.04 LTS on Dell Inspiron 600m"
date: 2010-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raphytaffy on 2010-05-19
Hey all, brand new to Ubuntu and thought I'd give it a shot today on an old laptop I had lying around. Pretty clueless about Linux builds in general and I've never used Ubuntu before so I'm not even sure I installed the proper version for my needs. Everything seems to be running great except for my wireless. Can anyone help me troubleshoot? Thanks!

EDIT: Checked a few threads and most of them suggested using **sudo lshw -c network** to help troubleshoot. Ran that command in terminal and it came back with this:

```
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:47:0c:22
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5705-v3.16 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:33:2d:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

How do I go about enabling my network since it seems disabled?

---

### Post by mr clark25 on 2010-05-19
is there a recommended driver? if so, you probably need to install it. you should be able to right-click the network icon and select enable/disable.

there is a command that is supposed to bring the wlan network up (run in terminal):
```

sudo ifconfig wlan0 up

```

if this doesn't fix the problem, please post the output of the command above.

---

### Post by raphytaffy on 2010-05-19
Absolute noob here, but did some more digging and found this thread:

[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

Followed those steps and everything is up and running just fine. Typing on Chrome on Ubuntu right now!

---

### Post by raphytaffy on 2010-05-27
Had this solved a while back and things were running smooth until I suspended my system. Upon waking up, wireless is now disabled and I can't seem to enable it again. Wireless function on my keyboard doesn't do the trick. Anyone know a nifty command to get this running again?

---

### Post by mr clark25 on 2010-05-27
do you get any output when you run:
```

sudo ifconfig wlan0 up

```

---

### Post by raphytaffy on 2010-05-27
Nope, no output.

---

### Post by AcidMoon on 2010-05-27
This is a long shot but I use one method to disable my wireless on purpose! I can't see this being automatically created by the system but do you have any entries for:
gksu gedit /etc/modprobe.d/blacklist
Anything like "blacklist ipw2200" ??

---

### Post by raphytaffy on 2010-05-28
Nope, more help please?

---

### Post by ugm6hr on 2010-05-29
Hard to know what's happened.  maybe give us the lshw output again?

---

### Post by raphytaffy on 2010-05-29
```
  *-network:0 DISABLED    
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:47:0c:22
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=5705-v3.16 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:33:2d:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

Hope this helps. Both ethernet and wireless seems to be disabled.

---

### Post by ugm6hr on 2010-05-30
> **raphytaffy said:**
> Both ethernet and wireless seems to be disabled.

Yes - I presume that means you can't connect by wire either now?

Are you dual-booting (i.e. still have Windows on the laptop)?  If so - see Q9 in the Wifi help link below.

Also - post output of:
```
ifconfig
iwconfig
```

See if there are any clues there, but I've never encountered Ubuntu switching off networking, which doesn't re-endable following a reboot.

Only other thing to check is in BIOS settings - see if the network cards are enabled there.

---

### Post by raphytaffy on 2010-05-30
```
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40586 (40.5 KB)  TX bytes:40586 (40.5 KB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

LAN Controller and Wireless are enabled in BIOS. Can't seem to pinpoint the issue.

---

### Post by ugm6hr on 2010-05-30
> **raphytaffy said:**
> LAN Controller and Wireless are enabled in BIOS. Can't seem to pinpoint the issue.

Are you dual-booting Windows?

---

### Post by raphytaffy on 2010-05-30
No, sir. Strictly Ubuntu.

---

### Post by ugm6hr on 2010-05-30
I presume that when you right-click Network Manager icon, that Networking, Wifi etc is enabled?

If so, I'm stuck.

It may be necessary to try enabling networking without Network Manager - it might be NM causing the problem, although I have never encountered such an issue myself that wasn't righted by a reboot.

---

### Post by raphytaffy on 2010-05-30
Wow. I never even tried to right-click the icon. Thanks!

---

### Post by ugm6hr on 2010-05-30
> **raphytaffy said:**
> Wow. I never even tried to right-click the icon. Thanks!

Must remember in future.... Start simple.

Glad you got it sorted, and learned something new!

---

### Post by Guitar John on 2010-05-30
I know why they do it, but it is a bit frustrating that you need a working internet connection to enable the Broadcomm 43xx drivers for the wireless connection.

---

### Post by ugm6hr on 2010-05-30
> **Guitar John said:**
> I know why they do it, but it is a bit frustrating that you need a working internet connection to enable the Broadcomm 43xx drivers for the wireless connection.

Not strictly true - you can download and install the driver manually.  It's just harder than it should be.

---

### Post by Guitar John on 2010-05-30
> **ugm6hr said:**
> Not strictly true - you can download and install the driver manually.  It's just harder than it should be.

Is the driver on the Ubuntu install disc?

---

### Post by ugm6hr on 2010-05-31
> **Guitar John said:**
> Is the driver on the Ubuntu install disc?

Don't know. Must be somewhere, since the LiveUSB works with Broadcom devices.  Nevertheless, it is not unusual to have to download / access drivers from elsewhere to install a new OS.

---

### Post by chaubathong on 2012-04-20
Just creat new /etc/sysconfig/network-scripts/ifcfg-eth* (* is an int number) with following information:
 
DEVICE=eth*
BOOTPROTO=none
HWADDR=[COLOR=red]00:0c:29:a8:73:3b <= MAC address of the DISABLE network card see below
[/COLOR]ONBOOT=yes
TYPE=Ethernet
NETMASK=255.255.255.0
IPADDR=192.168.137.10
GATEWAY=192.168.137.1

 
 *-network:0 DISABLE
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth1
       version: 10
       serial: [COLOR=red]00:0c:29:a8:73:45[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]finally perform network service restart[/COLOR]

---

