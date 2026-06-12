---
title: "Guys now i know my internet works, how do i do this????"
date: 2009-05-12
forum: General Help
---

### Post by dragonbeast25 on 2009-05-12
Ok i was bored so i poped ubuntu 9.04 live cd in laptop and plug ethernet cord, the modem detected the laptop, now i put in PC same ethernet port and same ethernet cord, it does not show? I think this is a sign of no power to the ethernet port on my PC how do i do this, i know it works but if i can get it working then i install ubuntu. Please guys

P.S Right out of the box laptop went straight to internet. Please reply very soon Bye, Using same port same modem same everything, but how do i confirge PC to put power to ethernet? Im guessing

---

### Post by dragonbeast25 on 2009-05-12
Please guys :(

---

### Post by dragonbeast25 on 2009-05-12
Comon guys i had trouble getting the internet to work even no it did on ubuntu, Im runing xp . And i pluged the laptop in and it worked so its somthing wrong with the ethernet port on the pc any ideas? But it works in xp?????

---

### Post by evermooingcow on 2009-05-12
A little confusing - trying to clarify:  You plugged the laptop directly into your modem and connected to the internet. You unplugged the laptop, plugged the PC to the modem and now you can't get internet on your PC?  Usually you need to power cycle the modem to have your ISP recognize that you have a new device on it.  -or- you can set the MAC address of your PC and laptop to be the same and you won't need to reboot the modem every time you change devices.

---

### Post by dragonbeast25 on 2009-05-12
Can you explain? Well the ports i plug in is from modem to a router. Router will work if pluged in laptop but not PC, CAn you explain how to do so, im not any good with ubuntu, Thanks :D

---

### Post by BslBryan on 2009-05-12
Hello, dragonbeast25. :-)

I'm not really understanding your problem.

Could you clarify?

EDIT: evermooingcow beat me to it. :P

---

### Post by dragonbeast25 on 2009-05-12
Ok Im running windows xp professional right now, i boot Live Cd Ubuntu 9.04 on my laptop Plug the LAN ethernet cord from my router to my laptop ethernet port on laptop, when it boots in it automaticly connects on my laptop and my modem glows up on that port(Meaning it found a computer)..

On my PC (Running now) i do same thing but in this case the router does not glow in live cd, only in windows xp And my ethernet cord is pluged in same place everything but sounds like my ethernet port is not sending power when running live cd. 

P.S my Laptop has xp aswell.

---

### Post by dragonbeast25 on 2009-05-12
So yeah.. If you guys and girls can help me i will install wubi then im going to install it permently and remove windows possibly. Bye guys reply soon im on here 24/7 :D i think :/

---

### Post by baseface on 2009-05-12
maybe your network card isnt supported on the live cd. you may have to actually install a driver or something to get it to work... which you cant do with the live cd.

---

### Post by tommynz1975 on 2009-05-12
can you go into terminal and put in

```
sudo lspci
``` to get into terminal  ..  go menus applicatoins --> Accesories --> terminal

and cut and paste the results, of your desktop system

---

### Post by dragonbeast25 on 2009-05-12
ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

---

### Post by dragonbeast25 on 2009-05-12
They're You go

---

### Post by dragonbeast25 on 2009-05-12
Please Reply Shortly.

---

### Post by dragonbeast25 on 2009-05-12
ughhhhhhhhh

---

### Post by geraldvillorente on 2009-05-12
execute this command on your PC and post the result here
```

ifconfig

```

Question:
Are you using router? from internet(DSL line) modem->router->PC/Laptop? Something like that?

---

### Post by dragonbeast25 on 2009-05-12
Bump

---

### Post by geraldvillorente on 2009-05-12
There is no problem on your ethernet port I think...it's on config maybe...

EDIT: need to know the exact scheme of your connection

---

### Post by dragonbeast25 on 2009-05-12
I do ifconfig all time 0 packets and everything. Line jack to modem to router wan from router LAN to pc

---

### Post by geraldvillorente on 2009-05-12
Ok...try to ping the gateway if there's a reply...if yes then the problem is not on the PC

EDIT: you can also renew IPAddress by doing this

```

sudo /etc/init.d/networking restart

```

failed to renew IP means that you are not connected to your router

---

### Post by dragonbeast25 on 2009-05-12
I cannot ping my router what next?

---

### Post by geraldvillorente on 2009-05-12
Next is try to renew IP address
```

sudo /etc/init.d/networking restart

```
then try to ping again

if none...

replace your ethernet cable...

if none...

get the IP details from your router using your machine where internet works and post here so that we can manually assign IP address to your network interface

---

### Post by pastalavista on 2009-05-12
I would try power down the router (unplug it) and shut down the PC. Then Plug the router back in and reboot the PC while it is connected to the router. That is IF you have the router set to automatic dhcp. Then go into network manager icon on the panel and see if you can see the connection and setup the security settings. To connect with the router, enter this IP in Firefox 192.168.1.1. This is how it should work but your router may be different. I have a Realtec ethernet card and it works fine.

---

### Post by dragonbeast25 on 2009-05-13
> **pastalavista said:**
> I would try power down the router (unplug it) and shut down the PC. Then Plug the router back in and reboot the PC while it is connected to the router. That is IF you have the router set to automatic dhcp. Then go into network manager icon on the panel and see if you can see the connection and setup the security settings. To connect with the router, enter this IP in Firefox 192.168.1.1. This is how it should work but your router may be different. I have a Realtec ethernet card and it works fine.
Did that nothing worked it did not reconize my ethernet port on pc still, i also tried unplug modem and router in live cd and plug back in, nothing. Some possible way i could install the ethernet driver or send power to it.
Somthing i notice on xp: Loading up my keyboard flashed POWER, my mouse FLASHED power, AND then my ethernet got reconized by my modem so in xp it sends power out not on my pc??

---

### Post by issih on 2009-05-13
This is very unlikely to be related to "power" as you refer to it, and the order of initialisation of hardware devices in XP is irrelevant to this problem.

IT is almost certainly either that the ethernet card's driver (kernel module) is not functioning correctly for your hardware, or you have a configuration problem.

Check that the system is set up in the same way as the laptop (e.g. go into network manager and ensure the pc is using dhcp assuming the laptop does that)

Once you have triple checked the network config we can look into other things.

What do you actually see in:

```
ifconfig -a
``` - post the output

and also:

```
sudo lshw -C network
```

Hope that helps

---

### Post by dragonbeast25 on 2009-05-13
Alright let me boot ubuntu

---

### Post by AgentZ86 on 2009-05-13
Check the power settings of your bios in setup.

If the hardware is connected the lights should be on no matter what the software is doing in my opinion.

When I plugin a PC to a computer with NIC card and turn on the computer the lights are connected no matter what.

So in your bios you may have some settings for power on all the time.

See if you have any power management settings which are turned on currently and turn off all the power management setting for now just to be sure this is not interfering with anything.

I would have suspected that at the min. if the power of your PC is turned on then you should have lights blinking on the laptops/pc/router modem etc. blinking all the time at least that what happens to all my computers and server.

Thats about all I know of it.

Assuming that all your doing is running windows xp on your laptop and then simply running the ubuntu CD live on the same exact setup then I would suspect something with the power settings in your bios.

That may not get you connected or configured properly but at least should show some signs that the NIC is connected to something.

If not, and you have a PCMCIA card slot you could get a super cheap NIC card on ebay or a USB wireless NIC connection which works very well also.

Check compatibility for this but that would be another solution if all else fails.

---

### Post by dragonbeast25 on 2009-05-13
ifconfig -a
sudo lshw -C network

Output For: IfConfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:1a:e5:cc  
          inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr d6:93:f3:ad:c5:31  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B

Output For: sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:1a:e5:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:93:f3:ad:c5:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dragonbeast25 on 2009-05-13
Well i really dont want to turn power off in bios lol :P, but i agree with you maby if somthing is curretnly turned off like (ETHERNET BLAHBLAHBLAH) then i just power on all time?

---

### Post by issih on 2009-05-13
Assuming you are using dhcp to configure your local  ip address, can you post the output of running:

```
dhclient eth0
```

Also you should try setting up a static ip to isolate whether the problem is caused by dhcp or something more fundamental.

---

### Post by dragonbeast25 on 2009-05-13
ubuntu@ubuntu:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

I did not have permission?? So it wouldnt work, BTW im on ubuntu 9.04

---

### Post by issih on 2009-05-13
Sorry forgot a sudo there..you need root privileges to run the dhcp client...

```
sudo dhclient eth0
```

Hope that helps

---

### Post by dragonbeast25 on 2009-05-13
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:09:1a:e5:cc
Sending on   LPF/eth0/00:11:09:1a:e5:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by dragonbeast25 on 2009-05-13
bump

---

### Post by issih on 2009-05-13
Try using a static ip address.

Get the ip address of your router (i.e. the number you enter to access its admin web page, e.g. 192.168.0.1 is mine)

Now pick a new number for the last digit (one that is less than 255). Ideally this number should be outside whatever range is reserved for dhcp in the router, have a poke around the settings to find out what that range is, just dont change anything if you are not sure.

In the network manager set the connection to use the newly chosen ip address, enter 255.255.255.0 as the subnet mask, and use the ip adress of the router for the gateway and the primary dns fields. Leave the secondary dns blank.

Now see if the connection works, dhcp clearly isn't for some reason

---

### Post by dragonbeast25 on 2009-05-13
Does not work. BTW i got the same router ip 192.168.0.1

Running WBR-1310 D-link router... HMM maby somhow in bios menu like the guy said power mangemnt because i think its the pc because my modem and router work with my laptop so its the pc but how do i enable it can i do somthing like sudo ifconfig eth0 up? because i did it and nothing happend i also tried $ sudo ifconfig eth0 up did not find BASH $ :COmmand not found.

---

### Post by dragonbeast25 on 2009-05-13
bump

---

### Post by Tipped OuT on 2009-05-13
[B]Go connect your laptop with the Ethernet wire.

Go to System< Preferneces< Network Connections.

Click on "Add" under the "Wired" tab. And make sure MTU is set to Automatic, and IPv4 settings is set to automatic (DHCP).

Make sure "802.1 for this connection" is unchecked also.

And go ahead and save it. Tell me what happens. :D[/B]

EDIT: If that doesn't work, google how to set your network settings to "Auto Ethernet". That's what fixed it for me.

---

### Post by dragonbeast25 on 2009-05-13
here more info

sudo lspci


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Detected 1800.021 MHz processor.
[    0.181371] ExtINT not setup in hardware but reported by MP table
[    0.329328] net_namespace: 776 bytes
[    0.360668] ACPI: Interpreter disabled.
[    0.362011] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.362066] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.363369] Bluetooth: Core ver 2.13
[    0.363369] Bluetooth: HCI device and connection manager initialized
[    0.363369] Bluetooth: HCI socket layer initialized
[    0.363369] NetLabel: Initializing
[    0.363369] NetLabel:  domain hash size = 128
[    0.363369] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.363369] NetLabel:  unlabeled traffic allowed by default
[    0.364834] pci 0000:00:1e.0: setting latency timer to 64
[    1.358871] cpufreq: No nForce2 chipset.
[    1.359161] audit: initializing netlink socket (disabled)
[    1.372842] msgmni has been set to 1718
[    1.732555] Driver 'sd' needs updating - please use bus_type methods
[    1.732573] Driver 'sr' needs updating - please use bus_type methods
[    1.732804] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.198211] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.216250] hub 1-0:1.0: 6 ports detected
[    2.216536] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.216831] hub 2-0:1.0: 2 ports detected
[    2.216981] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.217271] hub 3-0:1.0: 2 ports detected
[    2.217402] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.217715] hub 4-0:1.0: 2 ports detected
[    2.219671] EISA: Detected 0 cards.
[    2.221873] Bluetooth: L2CAP ver 2.11
[    2.221877] Bluetooth: L2CAP socket layer initialized
[    2.221882] Bluetooth: SCO (Voice Link) ver 0.6
[    2.221886] Bluetooth: SCO socket layer initialized
[    2.221943] Bluetooth: RFCOMM socket layer initialized
[    2.221957] Bluetooth: RFCOMM TTY layer initialized
[    2.221960] Bluetooth: RFCOMM ver 1.10
[    2.222408] rtc_cmos 00:03: setting system clock to 2009-05-13 15:27:21 UTC (1242228441)
[    2.262676] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.069050] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.081770] 8139too Fast Ethernet driver 0.9.28
[    3.083212] eth0: RealTek RTL8139 at 0xc800, 00:11:09:1a:e5:cc, IRQ 23
[    3.083216] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.477111] usb-storage: waiting for device to settle before scanning
[    5.305446] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.477631] usb-storage: device scan complete
[   66.217957] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   66.218396] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   66.435507] intel_rng: FWH not detected
[   68.098665] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   81.577479] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   81.577485] Bluetooth: BNEP filters: protocol multicast
[   89.246052] pci 0000:00:02.0: setting latency timer to 64
[   89.259423] [drm:i915_setparam] *ERROR* unknown parameter 4
[   89.259475] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   89.727048] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   90.533889] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  100.654861] eth0: no IPv6 routers present
[  101.842916] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
[  101.842920] NETDEV WATCHDOG: eth0 (8139too): transmit timed out
[  101.843046]  [<c04312f2>] ? netdev_drivername+0x32/0x40
[  101.843059]  [<c01568f3>] ? getnstimeofday+0x53/0x110
[  104.842990] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  104.842998] eth0: Tx queue start entry 4  dirty entry 0.
[  104.843003] eth0:  Tx descriptor 0 is 0008205a. (queue head)
[  104.843007] eth0:  Tx descriptor 1 is 0008204e.
[  104.843011] eth0:  Tx descriptor 2 is 00082046.
[  104.843015] eth0:  Tx descriptor 3 is 00082156.
[  104.843037] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  116.843725] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  116.843734] eth0: Tx queue start entry 4  dirty entry 0.
[  116.843740] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  116.843745] eth0:  Tx descriptor 1 is 0008205a.
[  116.843749] eth0:  Tx descriptor 2 is 00082046.
[  116.843753] eth0:  Tx descriptor 3 is 00082046.
[  116.843775] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  170.844875] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  170.844882] eth0: Tx queue start entry 4  dirty entry 0.
[  170.844887] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  170.844892] eth0:  Tx descriptor 1 is 00082156.
[  170.844896] eth0:  Tx descriptor 2 is 00082156.
[  170.844900] eth0:  Tx descriptor 3 is 00082156.
[  170.844922] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1



00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by dragonbeast25 on 2009-05-13
I tried it all never worked its somthing wrong with my ethernet card in my PC because everything else works on laptop ubuntu

.....................................................

---

### Post by dragonbeast25 on 2009-05-13
BuMp.>.>

---

### Post by dragonbeast25 on 2009-05-13
Bump

---

### Post by PRC09 on 2009-05-13
Sorry if I missed something here.So you have XP on your PC and you can connect and surf ok ,and when you run the live cd on the same machine you have no internet,is this correct??

---

### Post by dragonbeast25 on 2009-05-13
Yes, Somthing due to no power from my ethernet port on live cd, Ubuntu 9.04 Im guessing. :/

---

### Post by dragonbeast25 on 2009-05-13
BuMP

---

### Post by alphacrucis2 on 2009-05-13
> **dragonbeast25 said:**
> BuMp.>.>

Perhaps this is relevant. Wake-on-lan after shutdown setting:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496")

---

### Post by dragonbeast25 on 2009-05-13
> **alphacrucis2 said:**
> Perhaps this is relevant. Wake-on-lan after shutdown setting:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496")
Yes that is the bug i am having but i dont get how do fix it CAn you explain how to do this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798")

Please and thank you, i have same drivers as this bug and this should work , but can anyone explain that little easier, im running a live cd ?

---

### Post by issih on 2009-05-13
If that is what is causing your problem, the simplest solution is to boot into windows, go to device manager and open the properties of the network card. In there find the setting related to wake on lan, and ensure that it is set to allow wake on lan after windows is shut down.

Once that is done, reboot and see if ubuntu can now bring up the interface.

Hope that helps

---

### Post by dragonbeast25 on 2009-05-13
> **issih said:**
> if that is what is causing your problem, the simplest solution is to boot into windows, go to device manager and open the properties of the network card. In there find the setting related to wake on lan, and ensure that it is set to allow wake on lan after windows is shut down.

Once that is done, reboot and see if ubuntu can now bring up the interface.

Hope that helps
posting via live cd !!!!!!!! Thank you!!!!!!!!!!!! Hmm will that option effect my windows xp network because after that i went firefox on xp and it works.. Thanks 100 %!

---

### Post by AgentZ86 on 2009-05-14
Wake up on LAN good idea, and should not effect your windows use.

I think in the bios there is a seting for wakeup on lan Also which could be why you don't see the lights on your NIC and router showing a connection.

But likely driver issue, why not just find a NIC Com3 card on craigslist for free or something and you can put that in the PC and Ubuntu will pick it up no problem.

Also I'm assuming your using Hardwire on the PC and not wireless connection ?

---

