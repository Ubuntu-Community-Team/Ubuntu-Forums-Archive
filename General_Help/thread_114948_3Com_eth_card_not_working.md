---
title: "3Com eth card not working"
date: 2006-01-09
forum: General Help
---

### Post by features on 2006-01-09
Hi all,

I have had to swap NIC's on my laptop (my Xircom one died).  I am trying to use a 3Com Megahertz eth/modem card.  It is model **3CCFEM556 B**.  It is not on the hardware compatibility list on the [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards").

Ubuntu detects the card, and attempts to gain a connection.  Shortly after, the machine locks up until I eject the card.

/var/log/messages shows:

```
Jan 10 09:39:34 localhost kernel: [4295472.760000] eth0: interrupt(s) dropped!
Jan 10 09:39:40 localhost kernel: [4295479.089000]   ASIC rev 1,<6>eth0: 3Com 3c574 at io 0x300, irq 3, hw_addr 00:00:86:30:1D:A0.
Jan 10 09:39:40 localhost kernel: [4295479.116000]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
Jan 10 09:39:40 localhost kernel: [4295479.215000] ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
Jan 10 09:39:45 localhost kernel: [4295484.420000] eth0: remote fault detected
Jan 10 09:39:47 localhost kernel: [4295486.420000] eth0: found link beat
Jan 10 09:39:47 localhost kernel: [4295486.420000] eth0: autonegotiation complete: 100baseT-FD selected
Jan 10 09:39:47 localhost kernel: [4295486.420000] eth0: remote fault detected
Jan 10 09:40:11 localhost kernel: [4295510.244000] eth0: interrupt(s) dropped!
Jan 10 09:40:11 localhost kernel: [4295510.244000] eth0: command 0x5800 did not complete!
Jan 10 09:40:13 localhost last message repeated 31 times
```

And daemon.log seems to show that it's loading the drivers for the 3C357 series cards:

```
Jan 10 09:32:03 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Jan 10 09:32:03 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Jan 10 09:32:03 localhost dhclient: All rights reserved.
Jan 10 09:32:03 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Jan 10 09:32:03 localhost dhclient: 
Jan 10 09:32:03 localhost dhclient: sit0: unknown hardware address type 776
Jan 10 09:32:03 localhost dhclient: irda0: unknown hardware address type 783
Jan 10 09:32:04 localhost dhclient: sit0: unknown hardware address type 776
Jan 10 09:32:04 localhost dhclient: irda0: unknown hardware address type 783
Jan 10 09:32:04 localhost dhclient: Listening on LPF/eth0/00:00:86:30:1d:a0
Jan 10 09:32:04 localhost dhclient: Sending on   LPF/eth0/00:00:86:30:1d:a0
Jan 10 09:32:04 localhost dhclient: Sending on   Socket/fallback
Jan 10 09:32:04 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 10 09:32:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 10 09:32:13 localhost dhclient: receive_packet failed on eth0: Network is down
Jan 10 09:32:13 localhost cardmgr[7001]: executing: './network stop eth0'
Jan 10 09:32:13 localhost cardmgr[7001]: + eth0: error fetching interface information: Device not found
Jan 10 09:32:14 localhost cardmgr[7001]: + /sbin/ifdown: interface eth0 not configured
Jan 10 09:32:14 localhost cardmgr[7001]: executing: './serial stop ttyS2'
Jan 10 09:32:14 localhost cardmgr[7001]: executing: 'modprobe -r 3c574_cs'
Jan 10 09:32:14 localhost cardmgr[7001]: executing: 'modprobe -r serial_cs'
Jan 10 09:32:17 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Jan 10 09:32:17 localhost dhclient: send_packet: No such device
Jan 10 09:32:20 localhost cardmgr[7001]: socket 1: 3Com/Megahertz 3CCFEM556 Ethernet/Modem
Jan 10 09:32:20 localhost cardmgr[7001]: executing: 'modprobe 3c574_cs'
Jan 10 09:32:20 localhost cardmgr[7001]: executing: 'modprobe serial_cs'
Jan 10 09:32:20 localhost cardmgr[7001]: executing: './network start eth0'
Jan 10 09:32:21 localhost cardmgr[7001]: executing: './serial start ttyS2'
Jan 10 09:32:33 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Jan 10 09:32:36 localhost cardmgr[7001]: executing: './network stop eth0'
Jan 10 09:32:37 localhost cardmgr[7001]: + eth0: error fetching interface information: Device not found
Jan 10 09:32:37 localhost cardmgr[7001]: + /sbin/ifdown: interface eth0 not configured
Jan 10 09:32:37 localhost cardmgr[7001]: executing: './serial stop ttyS2'
Jan 10 09:32:37 localhost cardmgr[7001]: executing: 'modprobe -r 3c574_cs'
Jan 10 09:32:37 localhost cardmgr[7001]: executing: 'modprobe -r serial_cs'
Jan 10 09:32:54 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 10 09:32:54 localhost dhclient: send_packet: No such device
Jan 10 09:32:55 localhost cardmgr[7001]: socket 1: 3Com/Megahertz 3CCFEM556 Ethernet/Modem
Jan 10 09:32:55 localhost cardmgr[7001]: executing: 'modprobe 3c574_cs'
Jan 10 09:32:55 localhost cardmgr[7001]: executing: 'modprobe serial_cs'
Jan 10 09:32:55 localhost cardmgr[7001]: executing: './network start eth0'
Jan 10 09:32:56 localhost cardmgr[7001]: + /sbin/ifup: interface eth0 already configured
Jan 10 09:32:56 localhost cardmgr[7001]: executing: './serial start ttyS2'
Jan 10 09:33:04 localhost dhclient: No DHCPOFFERS received.
Jan 10 09:33:04 localhost dhclient: No working leases in persistent database - sleeping.
Jan 10 09:33:37 localhost cardmgr[7001]: executing: './network stop eth0'
Jan 10 09:33:37 localhost cardmgr[7001]: + eth0: error fetching interface information: Device not found
Jan 10 09:33:37 localhost cardmgr[7001]: + /sbin/ifdown: interface eth0 not configured
Jan 10 09:33:37 localhost cardmgr[7001]: executing: './serial stop ttyS2'
Jan 10 09:33:38 localhost cardmgr[7001]: executing: 'modprobe -r 3c574_cs'
Jan 10 09:33:38 localhost cardmgr[7001]: executing: 'modprobe -r serial_cs'
Jan 10 09:33:41 localhost cardmgr[7001]: socket 1: 3Com/Megahertz 3CCFEM556 Ethernet/Modem
Jan 10 09:33:41 localhost cardmgr[7001]: executing: 'modprobe 3c574_cs'
Jan 10 09:33:41 localhost cardmgr[7001]: executing: 'modprobe serial_cs'
Jan 10 09:33:41 localhost cardmgr[7001]: executing: './network start eth0'
Jan 10 09:33:42 localhost cardmgr[7001]: executing: './serial start ttyS2'
Jan 10 09:33:52 localhost cardmgr[7001]: executing: './network stop eth0'
```

Has anyone else had any luck with this particular card?  Or is this brick wall a bit thick and chunky? :p

---

### Post by features on 2006-01-10
bump...:D

---

### Post by JeremyWorst on 2006-07-20
Did you ever get this card working?  I have one too, and can see it in the Device Manager properly identified, but no response out of it.  It works in the same laptop, Dell C800, when I dual boot to Windows 2000, both LAN and MODEM, but neither in Dapper.  I have another card, a 3Com 3CXFE574BT, which works fine, but it's only a LAN card and has no modem.

---

### Post by features on 2006-07-20
Nah, in the end I scored a Xircom card off one of my co-workers, and have since upgraded to a newer machine.  The machine in question now has W2k on it, so I couldn't even go back and check, sorry.  :(

---

