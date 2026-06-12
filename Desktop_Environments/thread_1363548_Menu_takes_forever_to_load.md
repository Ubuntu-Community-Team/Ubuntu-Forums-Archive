---
title: "Menu takes forever to load"
date: 2009-12-24
forum: Desktop Environments
---

### Post by PoopyTheJ on 2009-12-24
When booting Ubuntu recently I've noticed it takes forever for the time and date and username and network interface icons to load. While it's loading I can't click on Applications, places or system, nothing happens. I'm running a Q6600 with 8Gb of RAM and I've got plenty of space on the HD's so I'm wondering what could be causing the problem. Here's the last ten minutes of my log files, I've just gotten a MagicJack for use when in windows, I suppose it could be that?
```

Dec 24 14:08:09 poopythej-desktop kernel: [   18.210679] type=1505 audit(1261681689.729:15): operation="profile_replace" pid=1005 name=/usr/lib/connman/scripts/dhclient-script
Dec 24 14:08:09 poopythej-desktop kernel: [   18.213223] type=1505 audit(1261681689.733:16): operation="profile_replace" pid=1006 name=/usr/bin/evince
Dec 24 14:08:09 poopythej-desktop kernel: [   18.221044] type=1505 audit(1261681689.741:17): operation="profile_replace" pid=1006 name=/usr/bin/evince-previewer
Dec 24 14:08:09 poopythej-desktop kernel: [   18.225651] type=1505 audit(1261681689.745:18): operation="profile_replace" pid=1006 name=/usr/bin/evince-thumbnailer
Dec 24 14:08:09 poopythej-desktop kernel: [   18.231905] type=1505 audit(1261681689.749:19): operation="profile_replace" pid=1008 name=/usr/lib/cups/backend/cups-pdf
Dec 24 14:08:09 poopythej-desktop kernel: [   18.232543] type=1505 audit(1261681689.749:20): operation="profile_replace" pid=1008 name=/usr/sbin/cupsd
Dec 24 14:08:09 poopythej-desktop kernel: [   18.234312] type=1505 audit(1261681689.753:21): operation="profile_replace" pid=1009 name=/usr/sbin/tcpdump
Dec 24 14:08:09 poopythej-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 24 14:08:09 poopythej-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 24 14:08:09 poopythej-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Dec 24 14:08:09 poopythej-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 24 14:08:09 poopythej-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  Wireless now enabled by radio killswitch
Dec 24 14:08:09 poopythej-desktop NetworkManager:    SCPlugin-Ifupdown: (137472752) ... get_connections.
Dec 24 14:08:09 poopythej-desktop NetworkManager:    SCPlugin-Ifupdown: (137472752) ... get_connections (managed=false): return empty list.
Dec 24 14:08:09 poopythej-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): carrier is OFF
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): now managed
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): bringing up device.
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): preparing device.
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec 24 14:08:09 poopythej-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0
Dec 24 14:08:09 poopythej-desktop kernel: [   18.303736] sky2 eth0: enabling interface
Dec 24 14:08:09 poopythej-desktop kernel: [   18.303863] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 24 14:08:09 poopythej-desktop avahi-daemon[894]: Network interface enumeration completed.
Dec 24 14:08:09 poopythej-desktop avahi-daemon[894]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 24 14:08:09 poopythej-desktop avahi-daemon[894]: Server startup complete. Host name is poopythej-desktop.local. Local service cookie is 2825839806.
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  modem-manager is now available
Dec 24 14:08:09 poopythej-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 24 14:08:09 poopythej-desktop NetworkManager: <info>  Trying to start the supplicant...
Dec 24 14:08:09 poopythej-desktop init: apport pre-start process (1087) terminated with status 1
Dec 24 14:08:09 poopythej-desktop cron[1090]: (CRON) INFO (pidfile fd = 3)
Dec 24 14:08:09 poopythej-desktop init: apport post-stop process (1104) terminated with status 1
Dec 24 14:08:09 poopythej-desktop anacron[1132]: Anacron 2.3 started on 2009-12-24
Dec 24 14:08:09 poopythej-desktop cron[1148]: (CRON) STARTUP (fork ok)
Dec 24 14:08:09 poopythej-desktop cron[1148]: (CRON) INFO (Running @reboot jobs)
Dec 24 14:08:09 poopythej-desktop acpid: client connected from 1173[107:114]
Dec 24 14:08:09 poopythej-desktop anacron[1132]: Normal exit (0 jobs run)
Dec 24 14:08:10 poopythej-desktop gdm-binary[895]: WARNING: Unable to find users: no seat-id found
Dec 24 14:08:10 poopythej-desktop kernel: [   18.625063] ppdev: user-space parallel port driver
Dec 24 14:08:10 poopythej-desktop acpid: client connected from 1280[0:0]
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-1
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Dec 24 14:08:10 poopythej-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Dec 24 14:08:10 poopythej-desktop kernel: [   19.106985] [fglrx] Firegl kernel thread PID: 1468
Dec 24 14:08:11 poopythej-desktop kernel: [   20.172219] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Dec 24 14:08:11 poopythej-desktop kernel: [   20.172345] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  dhclient started with pid 1469
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 24 14:08:11 poopythej-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Dec 24 14:08:11 poopythej-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 24 14:08:11 poopythej-desktop dhclient: All rights reserved.
Dec 24 14:08:11 poopythej-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 24 14:08:11 poopythej-desktop dhclient: 
Dec 24 14:08:11 poopythej-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Dec 24 14:08:11 poopythej-desktop dhclient: Listening on LPF/eth0/00:01:29:a5:48:6e
Dec 24 14:08:11 poopythej-desktop dhclient: Sending on   LPF/eth0/00:01:29:a5:48:6e
Dec 24 14:08:11 poopythej-desktop dhclient: Sending on   Socket/fallback
Dec 24 14:08:12 poopythej-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 24 14:08:12 poopythej-desktop kernel: [   20.650042] [fglrx] Gart USWC size:1279 M.
Dec 24 14:08:12 poopythej-desktop kernel: [   20.650044] [fglrx] Gart cacheable size:508 M.
Dec 24 14:08:12 poopythej-desktop kernel: [   20.650048] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Dec 24 14:08:12 poopythej-desktop kernel: [   20.650050] [fglrx] Reserved FB block: Unshared offset:fbfe000, size:402000 
Dec 24 14:08:12 poopythej-desktop kernel: [   20.650052] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
Dec 24 14:08:12 poopythej-desktop dhclient: DHCPOFFER of 192.168.0.199 from 192.168.0.1
Dec 24 14:08:12 poopythej-desktop dhclient: DHCPREQUEST of 192.168.0.199 on eth0 to 255.255.255.255 port 67
Dec 24 14:08:12 poopythej-desktop dhclient: DHCPACK of 192.168.0.199 from 192.168.0.1
Dec 24 14:08:12 poopythej-desktop dhclient: bound to 192.168.0.199 -- renewal in 33861 seconds.
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>    address 192.168.0.199
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>    gateway 192.168.0.1
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>    nameserver '192.168.0.1'
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>    domain name 'neo.rr.com'
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 24 14:08:12 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 24 14:08:12 poopythej-desktop avahi-daemon[894]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.199.
Dec 24 14:08:12 poopythej-desktop avahi-daemon[894]: New relevant interface eth0.IPv4 for mDNS.
Dec 24 14:08:12 poopythej-desktop avahi-daemon[894]: Registering new address record for 192.168.0.199 on eth0.IPv4.
Dec 24 14:08:13 poopythej-desktop avahi-daemon[894]: Registering new address record for fe80::201:29ff:fea5:486e on eth0.*.
Dec 24 14:08:13 poopythej-desktop console-kit-daemon[904]: WARNING: Couldn't read /proc/900/environ: Failed to open file '/proc/900/environ': No such file or directory
Dec 24 14:08:13 poopythej-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Dec 24 14:08:13 poopythej-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 24 14:08:13 poopythej-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Dec 24 14:08:13 poopythej-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 24 14:08:13 poopythej-desktop kernel: [   22.150250] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Dec 24 14:08:13 poopythej-desktop kernel: [   22.154413] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Dec 24 14:08:14 poopythej-desktop ntpdate[1598]: step time server 91.189.94.4 offset 0.765074 sec
Dec 24 14:08:22 poopythej-desktop kernel: [   30.620006] eth0: no IPv6 routers present
Dec 24 14:08:24 poopythej-desktop kernel: [   32.380011] usb 4-2: device descriptor read/64, error -110
Dec 24 14:08:24 poopythej-desktop kernel: [   32.596010] usb 4-2: new full speed USB device using uhci_hcd and address 3
Dec 24 14:08:39 poopythej-desktop kernel: [   47.708010] usb 4-2: device descriptor read/64, error -110
Dec 24 14:08:40 poopythej-desktop gnome-session[1499]: devkit-power-gobject-WARNING: Couldn't enumerate devices: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Dec 24 14:08:55 poopythej-desktop kernel: [   62.924012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:08:55 poopythej-desktop kernel: [   63.140010] usb 4-2: new full speed USB device using uhci_hcd and address 4
Dec 24 14:09:05 poopythej-desktop kernel: [   73.548010] usb 4-2: device not accepting address 4, error -110
Dec 24 14:09:05 poopythej-desktop kernel: [   73.660009] usb 4-2: new full speed USB device using uhci_hcd and address 5
Dec 24 14:09:10 poopythej-desktop gnome-session[1499]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3/3-1
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 050D:0815
Dec 24 14:09:16 poopythej-desktop kernel: [   84.068011] usb 4-2: device not accepting address 5, error -110
Dec 24 14:09:16 poopythej-desktop kernel: [   84.068026] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:09:16 poopythej-desktop kernel: [   84.308010] usb 5-2: new low speed USB device using uhci_hcd and address 2
Dec 24 14:09:16 poopythej-desktop kernel: [   84.482177] usb 5-2: configuration #1 chosen from 1 choice
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop kernel: [   84.502347] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input7
Dec 24 14:09:16 poopythej-desktop kernel: [   84.502422] generic-usb 0003:046D:C506.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3/3-1
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 050D:0815
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 24 14:09:16 poopythej-desktop udev-configure-printer: Failed to get parent
Dec 24 14:09:16 poopythej-desktop anacron[1847]: Anacron 2.3 started on 2009-12-24
Dec 24 14:09:16 poopythej-desktop anacron[1847]: Normal exit (0 jobs run)
Dec 24 14:09:47 poopythej-desktop kernel: [  115.080011] usb 4-2: new full speed USB device using uhci_hcd and address 6
Dec 24 14:10:02 poopythej-desktop kernel: [  130.192012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:10:17 poopythej-desktop kernel: [  145.408012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:10:17 poopythej-desktop kernel: [  145.624010] usb 4-2: new full speed USB device using uhci_hcd and address 7
Dec 24 14:10:33 poopythej-desktop kernel: [  160.737509] usb 4-2: device descriptor read/64, error -110
Dec 24 14:10:48 poopythej-desktop kernel: [  175.952012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:10:48 poopythej-desktop kernel: [  176.168010] usb 4-2: new full speed USB device using uhci_hcd and address 8
Dec 24 14:10:58 poopythej-desktop kernel: [  186.576009] usb 4-2: device not accepting address 8, error -110
Dec 24 14:10:58 poopythej-desktop kernel: [  186.688011] usb 4-2: new full speed USB device using uhci_hcd and address 9
Dec 24 14:11:09 poopythej-desktop kernel: [  197.096010] usb 4-2: device not accepting address 9, error -110
Dec 24 14:11:09 poopythej-desktop kernel: [  197.096024] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:11:40 poopythej-desktop kernel: [  228.064012] usb 4-2: new full speed USB device using uhci_hcd and address 10
Dec 24 14:11:55 poopythej-desktop kernel: [  243.176011] usb 4-2: device descriptor read/64, error -110
Dec 24 14:12:10 poopythej-desktop kernel: [  258.392010] usb 4-2: device descriptor read/64, error -110
Dec 24 14:12:10 poopythej-desktop kernel: [  258.608011] usb 4-2: new full speed USB device using uhci_hcd and address 11
Dec 24 14:12:26 poopythej-desktop kernel: [  273.724012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:12:41 poopythej-desktop kernel: [  288.944019] usb 4-2: device descriptor read/64, error -110
Dec 24 14:12:41 poopythej-desktop kernel: [  289.160018] usb 4-2: new full speed USB device using uhci_hcd and address 12
Dec 24 14:12:51 poopythej-desktop kernel: [  299.568017] usb 4-2: device not accepting address 12, error -110
Dec 24 14:12:51 poopythej-desktop kernel: [  299.681521] usb 4-2: new full speed USB device using uhci_hcd and address 13
Dec 24 14:13:02 poopythej-desktop kernel: [  310.088017] usb 4-2: device not accepting address 13, error -110
Dec 24 14:13:02 poopythej-desktop kernel: [  310.088032] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:13:33 poopythej-desktop kernel: [  341.068032] usb 4-2: new full speed USB device using uhci_hcd and address 14
Dec 24 14:13:48 poopythej-desktop kernel: [  356.180024] usb 4-2: device descriptor read/64, error -110
Dec 24 14:14:03 poopythej-desktop kernel: [  371.396013] usb 4-2: device descriptor read/64, error -110
Dec 24 14:14:03 poopythej-desktop kernel: [  371.612010] usb 4-2: new full speed USB device using uhci_hcd and address 15
Dec 24 14:14:19 poopythej-desktop kernel: [  386.724017] usb 4-2: device descriptor read/64, error -110
Dec 24 14:14:34 poopythej-desktop kernel: [  401.944517] usb 4-2: device descriptor read/64, error -110
Dec 24 14:14:34 poopythej-desktop kernel: [  402.156011] usb 4-2: new full speed USB device using uhci_hcd and address 16
Dec 24 14:14:44 poopythej-desktop kernel: [  412.564011] usb 4-2: device not accepting address 16, error -110
Dec 24 14:14:44 poopythej-desktop kernel: [  412.676010] usb 4-2: new full speed USB device using uhci_hcd and address 17
Dec 24 14:14:55 poopythej-desktop kernel: [  423.084019] usb 4-2: device not accepting address 17, error -110
Dec 24 14:14:55 poopythej-desktop kernel: [  423.084033] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:15:26 poopythej-desktop kernel: [  454.064012] usb 4-2: new full speed USB device using uhci_hcd and address 18
Dec 24 14:15:41 poopythej-desktop kernel: [  469.176012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:15:56 poopythej-desktop kernel: [  484.392014] usb 4-2: device descriptor read/64, error -110
Dec 24 14:15:56 poopythej-desktop kernel: [  484.608012] usb 4-2: new full speed USB device using uhci_hcd and address 19
Dec 24 14:16:12 poopythej-desktop kernel: [  499.721061] usb 4-2: device descriptor read/64, error -110
Dec 24 14:16:27 poopythej-desktop kernel: [  514.936012] usb 4-2: device descriptor read/64, error -110
Dec 24 14:16:27 poopythej-desktop kernel: [  515.152010] usb 4-2: new full speed USB device using uhci_hcd and address 20
Dec 24 14:16:37 poopythej-desktop kernel: [  525.560014] usb 4-2: device not accepting address 20, error -110
Dec 24 14:16:37 poopythej-desktop kernel: [  525.672010] usb 4-2: new full speed USB device using uhci_hcd and address 21
Dec 24 14:16:48 poopythej-desktop kernel: [  536.080011] usb 4-2: device not accepting address 21, error -110
Dec 24 14:16:48 poopythej-desktop kernel: [  536.080025] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:17:01 poopythej-desktop CRON[1966]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 24 14:17:19 poopythej-desktop kernel: [  567.076029] usb 4-2: new full speed USB device using uhci_hcd and address 22
Dec 24 14:17:34 poopythej-desktop kernel: [  582.188013] usb 4-2: device descriptor read/64, error -110
Dec 24 14:17:49 poopythej-desktop kernel: [  597.404013] usb 4-2: device descriptor read/64, error -110
Dec 24 14:17:49 poopythej-desktop kernel: [  597.620011] usb 4-2: new full speed USB device using uhci_hcd and address 23
Dec 24 14:18:05 poopythej-desktop kernel: [  612.732013] usb 4-2: device descriptor read/64, error -110
Dec 24 14:18:20 poopythej-desktop kernel: [  627.948027] usb 4-2: device descriptor read/64, error -110
Dec 24 14:18:20 poopythej-desktop kernel: [  628.164018] usb 4-2: new full speed USB device using uhci_hcd and address 24
Dec 24 14:18:30 poopythej-desktop kernel: [  638.572012] usb 4-2: device not accepting address 24, error -110
Dec 24 14:18:30 poopythej-desktop kernel: [  638.684012] usb 4-2: new full speed USB device using uhci_hcd and address 25
Dec 24 14:18:41 poopythej-desktop kernel: [  649.092010] usb 4-2: device not accepting address 25, error -110
Dec 24 14:18:41 poopythej-desktop kernel: [  649.092024] hub 4-0:1.0: unable to enumerate USB device on port 2
Dec 24 14:19:12 poopythej-desktop kernel: [  680.064021] usb 4-2: new full speed USB device using uhci_hcd and address 26
Dec 24 14:19:27 poopythej-desktop kernel: [  695.180013] usb 4-2: device descriptor read/64, error -110
Dec 24 14:19:42 poopythej-desktop kernel: [  710.396016] usb 4-2: device descriptor read/64, error -110
Dec 24 14:19:42 poopythej-desktop kernel: [  710.612015] usb 4-2: new full speed USB device using uhci_hcd and address 27
Dec 24 14:19:58 poopythej-desktop kernel: [  725.725512] usb 4-2: device descriptor read/64, error -110
```

---

