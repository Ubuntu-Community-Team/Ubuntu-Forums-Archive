---
title: "wireless problem in inspiron6400"
date: 2009-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manu jain on 2009-05-16
my system freezes as soon as i switch on my wireless....and if wireless switch is on then my system does not even boot in ubuntu.....

i have installed windows xp sp3 home edition along with ubuntu 8.10

help???

---

### Post by coffeeaddict22 on 2009-05-16
Hi,
I take it you can get into Ubuntu without any trouble, so long as the wireless is off?
Does the wireless work fine in Windows?
Was it working?  What did you do prior to it breaking?
And, assuming you can get into Ubuntu, a couple of things.  Can you post back the output of ```
lshw -C network
iwconfig
``` 
They're two separate commands, and hopefully will point out the problem.
Also, make it freeze, reboot, and post back the output of ```
dmesg
```If you can figure out the relevant bit (the numbers on the left of the output are seconds, so just look for where they change to see the reboot; it'll be just before that) just post that back.  Put it between code brackets (the # button at the top of the box here) to make it easier to read.

---

### Post by manu jain on 2009-05-17
mj@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:82:7f:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w39n51 driverversion=1.53+Intel,12/04/2005,10.1.0.13 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:19:57:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.18.71 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:46:01:c2:7e:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by manu jain on 2009-05-17
mj@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=35613 B   Fragment thr=35613 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by manu jain on 2009-05-17
my wireless works absolutely fine in windows xp but not in ubuntu 8.10..[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by coffeeaddict22 on 2009-05-17
Your problem is the driver.  You're running the windows driver under ndiswrapper, but there's a driver for your wireless card in the kernel; unload ndiswrapper (sudo modprobe -r ndiswrapper), and see if that's all it takes.  if not, type ```
lsmod |grep iwlwifi
```; if there's no output from that, ```
modprobe iwlwifi
``` should do it.  See [the Intel wireless site here ]("http://intellinuxwireless.org/") for more details.

If it's not right after that, reboot, then run ```
lshw -C network
``` again, followed by ```
iwconfig
nm-tool
```and post the results back.

---

### Post by manu jain on 2009-05-18
i installed the wireless driver.....but....again when i switched on my wireless......everything froze.....sandstill

---

### Post by manu jain on 2009-05-18
mj@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:ax:ax:ax:ax:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w39n51 driverversion=1.53+Intel,12/04/2005,10.1.0.13 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:yy:yy:yy:yy:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.18.71 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:yy:yy:yy:yy:b4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
mj@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=35613 B   Fragment thr=35613 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mj@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            NULL(info.linux.driver)
  State:             connected
  Default:           yes
  HW Address:        00:zz:zz:zz:zz:82

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.18.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.18.1

    DNS:             192.168.4.12
    DNS:             192.168.4.10


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             unavailable
  Default:           no
  HW Address:        00:ax:ax:ax:ax:3D

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by coffeeaddict22 on 2009-05-19
You're still running ndiswrapper (have a look at the driver line in nm-tool for your wireless).  You need to do the ndiswrapper removal- ```
sudo modprobe -r ndiswrapper
``` and then see what you've got.  Currently there's two drivers installed, they're competing for your card... bad things happen.  You need to remove one.

---

