---
title: "Desktop Freezing randomly"
date: 2017-04-16
forum: Desktop Environments
---

### Post by Wizball on 2017-04-16
This is really bugging me and only started to happen since I updated to the lasted release of ubuntu.
The  desk top will freeze for no apparent reason at random occasions.  By  this I mean I can move the mouse but not interact with anything.
Sometimes it will let me drop out using ctl alt F1 and when I come back sometimes it has unfrozen.
Other times I have to close all my windows one by one then it will let me interact again with the windows in other ways.
I have been trying to see if I can find a patter to the problem but I cannot.
Any help in tracking down the issue is much appreciated
below is all the information I can think of that might help
Please excuse spelling or gamma I am dyslexic and know I get it wrong sometimes.
Many thanks
Peter 
```
linux version 4.7.0-040700-generic
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
XFCE Version 4.12
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
    Subsystem: Hewlett-Packard Company RS880M [Mobility Radeon HD 4225/4250]
    Kernel driver in use: radeon
```

---

### Post by ajgreeny on 2017-04-16
For start, where did that 4.7.0-040700-generic kernel come from?

It is no longer in the repos for 16.04 so you should really upgrade your kernel by running commands ```
sudo apt-get update
sudo apt-get dist-upgrade
```
The **dist-upgrade** command will not move your system to another version, so don't worry about that, but it should update the kernel you are using to a supported version which a simple **upgrade** will not.
See [https://ubuntuforums.org/showthread.php?t=2267752](https://ubuntuforums.org/showthread.php?t=2267752) for the fuller explanation.
I am not certain which kernel you will get to as you are starting with an unusual version, but try it and report back your new kernel version.

---

### Post by Wizball on 2017-04-17
Hi

ran the commands and got this

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  php7.1-common php7.1-xml
The following packages will be upgraded:
  libapache2-mod-php7.0 php-common php-xml php7.0-cli php7.0-common
  php7.0-json php7.0-opcache php7.0-readline php7.0-xml
9 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,627 kB of archives.
After this operation, 5,209 kB of additional disk space will be used.

Looks like all I will get is the php upgrades which I do not want as it will break a couple of old websites I maintain.

many thanks
Peter

---

### Post by flocculant on 2017-04-17
When it hangs - if you can get to vt1, login and check logs there.

```
journalctl -n 10
``` to see the last 10 journalctl entries

```
dmesg | tail -n 10
``` to see the last 10 dmesg entries

```
cat /var/log/syslog | tail -n 10
``` to see the last 10 syslog entries

If it proves elusive to be able to get to a vt, you can set so that journalctl's logs are persistent across boots.

```
sudo mkdir -p /var/log/journal
``` creates a folder for the logs

OR

```
pkexec mousepad /etc/systemd/journald.conf
``` to edit the .conf file

Set the Storage line to:

```
[Journal]
Storage=persistent
...
```

Maybe also check .xsession-errors in your home folder.


That aside - you're still going to need to deal with the kernel issue. 

Possibly by installing the 16.04 HWE Stacks - check out the wiki pages, [Enablement]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus") and the specific 16.04 [page]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

---

### Post by Wizball on 2017-04-20
Hi 

Managed to update the kernel now running 4.10.11-041011-generic

Lest see how that help

thanks

---

### Post by Wizball on 2017-04-20
Hi

ok I did the date as was suggested and the problem just occurred again I piped the results of the logs as suggested.

I am not good enough to see what is going on can anyone else?

Many thanks
Peter

**Journal**
-- Logs begin at Thu 2017-04-20 09:26:23 BST, end at Thu 2017-04-20 12:12:10 BST. --
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=207224 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=314643 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=289263 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:10:30 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=207224 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Apr 20 12:10:53 home-svr1 kernel: usb 5-1.3: new full-speed USB device number 8 using ohci-pci
Apr 20 12:10:53 home-svr1 kernel: usb 5-1.3: New USB device found, idVendor=046d, idProduct=c52b
Apr 20 12:10:53 home-svr1 kernel: usb 5-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 20 12:10:53 home-svr1 kernel: usb 5-1.3: Product: USB Receiver
Apr 20 12:10:53 home-svr1 kernel: usb 5-1.3: Manufacturer: Logitech
Apr 20 12:10:53 home-svr1 kernel: logitech-djreceiver 0003:046D:C52B.0015: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1.3/input2
Apr 20 12:10:53 home-svr1 mtp-probe[10821]: checking bus 5, device 8: "/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1.3"
Apr 20 12:10:53 home-svr1 mtp-probe[10821]: bus: 5, device: 8 was not an MTP device
Apr 20 12:10:53 home-svr1 kernel: input: Logitech Performance MX as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1.3/5-1.3:1.2/0003:046D:C52B.0015/0003:046D:101A.0016/input/input8
Apr 20 12:10:53 home-svr1 kernel: logitech-hidpp-device 0003:046D:101A.0016: input,hidraw3: USB HID v1.11 Mouse [Logitech Performance MX] on usb-0000:00:13.0-1.3:1
Apr 20 12:10:53 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=314643 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:10:53 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=289263 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Apr 20 12:10:53 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:12:10 home-svr1 kernel: [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=20882 PROTO=2 

**dmesg**
[ 9868.555334] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9868.555355] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=207224 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9868.565765] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=314643 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9868.565811] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=289263 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9868.565852] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9868.565890] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=207224 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9891.676867] usb 5-1.3: new full-speed USB device number 8 using ohci-pci
[ 9891.805338] usb 5-1.3: New USB device found, idVendor=046d, idProduct=c52b
[ 9891.805345] usb 5-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9891.805350] usb 5-1.3: Product: USB Receiver
[ 9891.805353] usb 5-1.3: Manufacturer: Logitech
[ 9891.827642] logitech-djreceiver 0003:046D:C52B.0015: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1.3/input2
[ 9892.065367] input: Logitech Performance MX as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1.3/5-1.3:1.2/0003:046D:C52B.0015/0003:046D:101A.0016/input/input8
[ 9892.066118] logitech-hidpp-device 0003:046D:101A.0016: input,hidraw3: USB HID v1.11 Mouse [Logitech Performance MX] on usb-0000:00:13.0-1.3:1
[ 9892.083252] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=314643 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9892.083284] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=289263 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9892.083306] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9968.613239] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=20882 PROTO=2 
[ 9973.623467] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 9973.670842] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:26:08:b1:66:b4:08:00 SRC=192.168.1.8 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=44995 PROTO=2 

[B]syslog
[/B]Apr 20 12:10:53 home-svr1 kernel: [ 9892.066118] logitech-hidpp-device 0003:046D:101A.0016: input,hidraw3: USB HID v1.11 Mouse [Logitech Performance MX] on usb-0000:00:13.0-1.3:1
Apr 20 12:10:53 home-svr1 kernel: [ 9892.083252] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=314643 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:10:53 home-svr1 kernel: [ 9892.083284] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2a00:23c4:309e:6100:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=289263 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Apr 20 12:10:53 home-svr1 kernel: [ 9892.083306] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:a2b3:ccff:fedf:27f1 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586783 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Apr 20 12:12:10 home-svr1 kernel: [ 9968.613239] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=20882 PROTO=2 
Apr 20 12:12:15 home-svr1 kernel: [ 9973.623467] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Apr 20 12:12:15 home-svr1 kernel: [ 9973.670842] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:26:08:b1:66:b4:08:00 SRC=192.168.1.8 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=44995 PROTO=2 
Apr 20 12:13:10 home-svr1 kernel: [10029.291591] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19525 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:10 home-svr1 kernel: [10029.294056] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19526 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:10 home-svr1 kernel: [10029.294097] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=680 TOS=0x00 PREC=0x00 TTL=1 ID=19527 PROTO=UDP SPT=60039 DPT=3702 LEN=660 
Apr 20 12:13:10 home-svr1 kernel: [10029.297469] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19528 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:10 home-svr1 kernel: [10029.351775] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=680 TOS=0x00 PREC=0x00 TTL=1 ID=19529 PROTO=UDP SPT=60039 DPT=3702 LEN=660 
Apr 20 12:13:11 home-svr1 kernel: [10029.472322] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19530 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:11 home-svr1 kernel: [10029.473640] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=680 TOS=0x00 PREC=0x00 TTL=1 ID=19531 PROTO=UDP SPT=60039 DPT=3702 LEN=660 
Apr 20 12:13:11 home-svr1 kernel: [10029.511178] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19532 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:11 home-svr1 kernel: [10029.534970] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=19533 PROTO=UDP SPT=60039 DPT=3702 LEN=664 
Apr 20 12:13:11 home-svr1 kernel: [10029.712942] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:68:14:01:0f:fe:2a:08:00 SRC=192.168.1.2 DST=239.255.255.250 LEN=680 TOS=0x00 PREC=0x00 TTL=1 ID=19534 PROTO=UDP SPT=60039 DPT=3702 LEN=660 
Apr 20 12:14:14 home-svr1 kernel: [10093.361376] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:38:d5:47:ba:33:90:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=20883 PROTO=2 
Apr 20 12:14:15 home-svr1 kernel: [10094.239289] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:30:18:4b:98:d0:08:00 SRC=192.168.1.15 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
Apr 20 12:14:16 home-svr1 kernel: [10094.476167] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:26:08:b1:66:b4:08:00 SRC=192.168.1.8 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=59011 PROTO=2

---

### Post by izznogooood on 2017-04-20
I have this issue with 17.04. I've never had this problems before. I have to exit to tty and kill Xorg...

It seems Compiz is the one to blame (on my machine), I use some extra Brighness and Saturation plugins, do you do anything with Compiz?

---

### Post by Wizball on 2017-04-21
I do not think that I use Compiz.

I can exit to tty and come back without doing anything and it will all start to work again.

Thanks

---

### Post by rbmorse on 2017-04-22
I see the same behavior, but I'm running Ubuntu-Gnome as a VMWare workstation VM on a Windows 10 host.  Disabling hardware acceleration for the VM seemed to mitigate the desktop freeze issue.

---

### Post by Wizball on 2017-04-23
hi 

thanks for the suggestion bt this is running on bare metal.

Many thanks

---

### Post by rbmorse on 2017-04-23
I understand, but you might try disabling hardware video acceleration and see if that mitigates the problem.

---

### Post by Wizball on 2017-04-27
> **rbmorse said:**
> I understand, but you might try disabling hardware video acceleration and see if that mitigates the problem.


Not sure how to do this as I do not have a Xorg.conf file and although tired to make one got problems with that.

---

### Post by flocculant on 2017-04-27
Nothing jumps out at me from the logs.

HAve you checked ram? 

There is an option to run memcheck from the grub menu [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

