---
title: "sudden reboot/reset after resume from suspend - Optiplex 755"
date: 2011-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ahoros on 2011-02-06
I use suspend to ram all the time.
I have installed Ubuntu 10.10 on my tried & true Optiplex 755
and it suspends fine 
but after resume (by pressing the power button) the PC comes back to life and I can log back in - but after about 1 minute 
the whole PC suddenly shuts down & reboots - just like somebody would press reset button.

I have no idea what might be the cause - but maybe it is video card?

see: fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)


Anybody had similar problem?



-----------------------------



fragment of my syslog:

Feb  6 08:48:32 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb  6 08:48:32 OPlex-755 kernel: [   20.089108] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Feb  6 08:48:32 OPlex-755 kernel: [   20.089258] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb  6 08:48:32 OPlex-755 NetworkManager[987]: <info> dhclient started with pid 1350
Feb  6 08:48:32 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb  6 08:48:32 OPlex-755 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb  6 08:48:32 OPlex-755 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb  6 08:48:32 OPlex-755 dhclient: All rights reserved.
Feb  6 08:48:32 OPlex-755 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb  6 08:48:32 OPlex-755 dhclient: 
Feb  6 08:48:32 OPlex-755 NetworkManager[987]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb  6 08:48:32 OPlex-755 gdm-session-worker[1353]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  6 08:48:32 OPlex-755 dhclient: Listening on LPF/eth0/00:21:9b:32:67:b4
Feb  6 08:48:32 OPlex-755 dhclient: Sending on   LPF/eth0/00:21:9b:32:67:b4
Feb  6 08:48:32 OPlex-755 dhclient: Sending on   Socket/fallback
Feb  6 08:48:32 OPlex-755 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully called chroot.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully dropped privileges.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully limited resources.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Running.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Watchdog thread running.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Canary thread running.
Feb  6 08:48:32 OPlex-755 polkitd[1371]: started daemon version 0.96 using authority implementation `local' version `0.96'
Feb  6 08:48:32 OPlex-755 anacron[1411]: Anacron 2.3 started on 2011-02-06
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1364 of process 1364 (n/a) owned by '113' high priority at nice level -11.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 1 threads of 1 processes of 1 users.
Feb  6 08:48:32 OPlex-755 anacron[1411]: Normal exit (0 jobs run)
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1419 of process 1364 (n/a) owned by '113' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 2 threads of 1 processes of 1 users.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1428 of process 1364 (n/a) owned by '113' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 3 threads of 1 processes of 1 users.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1429 of process 1364 (n/a) owned by '113' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 4 threads of 1 processes of 1 users.
Feb  6 08:48:32 OPlex-755 gdm-simple-greeter[1349]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Feb  6 08:48:33 OPlex-755 kernel: [   21.245506] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Feb  6 08:48:33 OPlex-755 kernel: [   21.247228] EXT4-fs (sda6): re-mounted. Opts: commit=0
Feb  6 08:48:33 OPlex-755 kernel: [   21.267609] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Feb  6 08:48:33 OPlex-755 avahi-daemon[989]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::221:9bff:fe32:67b4.
Feb  6 08:48:33 OPlex-755 avahi-daemon[989]: New relevant interface eth0.IPv6 for mDNS.
Feb  6 08:48:33 OPlex-755 avahi-daemon[989]: Registering new address record for fe80::221:9bff:fe32:67b4 on eth0.*.
Feb  6 08:48:35 OPlex-755 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb  6 08:48:35 OPlex-755 dhclient: DHCPOFFER of 192.168.1.134 from 192.168.1.1
Feb  6 08:48:35 OPlex-755 dhclient: DHCPREQUEST of 192.168.1.134 on eth0 to 255.255.255.255 port 67
Feb  6 08:48:35 OPlex-755 dhclient: DHCPACK of 192.168.1.134 from 192.168.1.1
Feb  6 08:48:35 OPlex-755 dhclient: bound to 192.168.1.134 -- renewal in 38615 seconds.
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> (eth0): DHCPv4 state changed preinit -> bound
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info>   address 192.168.1.134
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info>   prefix 24 (255.255.255.0)
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info>   gateway 192.168.1.1
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info>   hostname 'OPlex-755'
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info>   nameserver '192.168.1.1'
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb  6 08:48:35 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb  6 08:48:35 OPlex-755 avahi-daemon[989]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.134.
Feb  6 08:48:35 OPlex-755 avahi-daemon[989]: New relevant interface eth0.IPv4 for mDNS.
Feb  6 08:48:35 OPlex-755 avahi-daemon[989]: Registering new address record for 192.168.1.134 on eth0.IPv4.
Feb  6 08:48:36 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Feb  6 08:48:36 OPlex-755 NetworkManager[987]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb  6 08:48:36 OPlex-755 NetworkManager[987]: <info> Activation (eth0) successful, device activated.
Feb  6 08:48:36 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb  6 08:48:22 OPlex-755 ntpdate[1494]: step time server 91.189.94.4 offset -13.587341 sec
Feb  6 08:48:23 OPlex-755 gdm-session-worker[1353]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Feb  6 08:48:29 OPlex-755 kernel: [   30.528004] eth0: no IPv6 routers present
Feb  6 08:48:29 OPlex-755 gdm-session-worker[1353]: pam_sm_authenticate: Called
Feb  6 08:48:29 OPlex-755 gdm-session-worker[1353]: pam_sm_authenticate: username = [gosc]
Feb  6 08:48:29 OPlex-755 NetworkManager[987]: <error> [1296978509.939939] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Feb  6 08:48:30 OPlex-755 NetworkManager[987]: <error> [1296978510.18616] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Feb  6 08:48:31 OPlex-755 kernel: [   33.040893] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
Feb  6 08:48:31 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1608 of process 1608 (n/a) owned by '1001' high priority at nice level -11.
Feb  6 08:48:31 OPlex-755 rtkit-daemon[1366]: Supervising 5 threads of 2 processes of 2 users.
Feb  6 08:48:31 OPlex-755 modem-manager: (ttyS1) closing serial device...
Feb  6 08:48:31 OPlex-755 modem-manager: (ttyS1) opening serial device...
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1611 of process 1608 (n/a) owned by '1001' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 6 threads of 2 processes of 2 users.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1618 of process 1608 (n/a) owned by '1001' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 7 threads of 2 processes of 2 users.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1619 of process 1608 (n/a) owned by '1001' RT at priority 5.
Feb  6 08:48:32 OPlex-755 rtkit-daemon[1366]: Supervising 8 threads of 2 processes of 2 users.
Feb  6 08:48:33 OPlex-755 rtkit-daemon[1366]: Successfully made thread 1666 of process 1666 (n/a) owned by '1001' high priority at nice level -11.
Feb  6 08:48:33 OPlex-755 rtkit-daemon[1366]: Supervising 9 threads of 3 processes of 2 users.
Feb  6 08:48:33 OPlex-755 pulseaudio[1666]: pid.c: Daemon already running.
Feb  6 08:48:38 OPlex-755 modem-manager: (ttyS1) closing serial device...




Feb  6 09:17:01 OPlex-755 CRON[2163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)




Feb  6 10:09:29 OPlex-755 anacron[2226]: Anacron 2.3 started on 2011-02-06
Feb  6 10:09:29 OPlex-755 anacron[2226]: Normal exit (0 jobs run)
Feb  6 10:09:29 OPlex-755 kernel: [ 4891.294672] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Feb  6 10:09:29 OPlex-755 kernel: [ 4891.297825] EXT4-fs (sda6): re-mounted. Opts: commit=0
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> sleep requested (sleeping: no  enabled: yes)
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> sleeping or disabling...
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): now unmanaged
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): deactivating device (reason: 37).
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1350
Feb  6 10:09:30 OPlex-755 avahi-daemon[989]: Withdrawing address record for 192.168.1.134 on eth0.
Feb  6 10:09:30 OPlex-755 avahi-daemon[989]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.134.
Feb  6 10:09:30 OPlex-755 avahi-daemon[989]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): cleaning up...
Feb  6 10:09:30 OPlex-755 NetworkManager[987]: <info> (eth0): taking down device.
Feb  6 10:09:31 OPlex-755 avahi-daemon[989]: Interface eth0.IPv6 no longer relevant for mDNS.
Feb  6 10:09:31 OPlex-755 avahi-daemon[989]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::221:9bff:fe32:67b4.
Feb  6 10:09:31 OPlex-755 avahi-daemon[989]: Withdrawing address record for fe80::221:9bff:fe32:67b4 on eth0.
Feb  6 10:09:31 OPlex-755 NetworkManager[987]: <info> (eth0): carrier now OFF (device state 1)
Feb  6 10:09:31 OPlex-755 kernel: [ 4892.625537] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
Feb  6 10:09:31 OPlex-755 kernel: [ 4892.909847] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000066





Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: The canary thread is apparently starving. Taking action.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.209826] PM: Syncing filesystems ... done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.210583] PM: Preparing system for mem sleep
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.210588] Freezing user space processes ... (elapsed 0.01 seconds) done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.224262] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.240260] PM: Entering mem sleep
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.240285] Suspending console(s) (use no_console_suspend to debug)
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.240579] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242192] serial 00:06: disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242279] [fglrx] IRQ 46 Disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242310] [fglrx] Preparing suspend fglrx in kernel.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242314] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242331] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242357] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242966] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242972] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246433] e1000e 0000:00:19.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246440] e1000e 0000:00:19.0: PME# enabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246452]  pci0000:00: wake-up capability enabled by ACPI
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246492] ACPI handle has no context!
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.256285] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.260284] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344643] HDA Intel 0000:00:1b.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344682] ACPI handle has no context!
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344715] HDA Intel 0000:01:00.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344759] ACPI handle has no context!
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.360256] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.873 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.360261] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 118.051 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.361897] sd 2:0:0:0: [sda] Stopping disk
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632898] PM: suspend of drv:sd dev:2:0:0:0 complete after 392.323 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632903] PM: suspend of drv:scsi dev:target2:0:0 complete after 392.293 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632908] PM: suspend of drv:scsi dev:host2 complete after 392.249 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658159] [fglrx] Suspending fglrx in kernel completed.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658162] [fglrx] Power down the ASIC .
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658198] PM: suspend of drv:fglrx_pci dev:0000:01:00.0 complete after 415.967 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658220] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 411.716 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744009] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 501.741 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744018] PM: suspend of drv: dev:pci0000:00 complete after 497.497 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744025] PM: suspend of devices complete after 503.519 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744027] PM: suspend devices took 0.504 seconds
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.776092] PM: late suspend of devices complete after 32.061 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.776929] ACPI: Preparing to enter system sleep state S3
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.778430] PM: Saving platform NVS memory
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.785214] Disabling non-boot CPUs ...
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.788355] Broke affinity for irq 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.788363] Broke affinity for irq 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.892016] CPU 1 is now offline
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.892019] SMP alternatives: switching to UP code
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] Back to C!
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] PM: Restoring platform NVS memory
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] Enabling non-boot CPUs ...
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] SMP alternatives: switching to SMP code
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.902325] Booting Node 0 Processor 1 APIC 0x1
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897044] Initializing CPU#1
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.032257] CPU1 is up
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.033093] ACPI: Waking up from system sleep state S3
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.038243] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1 - docking
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053562] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0xa0100, writing 0xa010b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053569] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053572] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053588] pci 0000:00:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053595] pci 0000:00:03.0: restoring config space at offset 0x4 (was 0xfedad004, writing 0xf0200804)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053605] pci 0000:00:03.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053613] pci 0000:00:03.2: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053627] serial 0000:00:03.3: restoring config space at offset 0x5 (was 0x0, writing 0xfebda000)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053630] serial 0000:00:03.3: restoring config space at offset 0x4 (was 0x1, writing 0xec99)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053633] serial 0000:00:03.3: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053647] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053656] e1000e 0000:00:19.0: restoring config space at offset 0x6 (was 0x1, writing 0xecc1)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053659] e1000e 0000:00:19.0: restoring config space at offset 0x5 (was 0x0, writing 0xfebdb000)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053662] e1000e 0000:00:19.0: restoring config space at offset 0x4 (was 0x0, writing 0xfebe0000)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053667] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053682] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053696] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053708] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x205)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053722] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053739] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x305)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053752] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xfebd9c00)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053757] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053778] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053788] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xff97c004, writing 0xfebdc004)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053791] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053810] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053817] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053820] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe80fe80)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053823] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x1010)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053826] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x20200)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053831] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053835] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053857] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053871] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053883] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x205)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053896] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053908] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053922] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053939] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053952] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xff980800)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053957] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053977] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053981] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053984] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.053990] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054033] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054040] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0xff970000, writing 0xf0200000)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054048] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054075] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xfebd9b04)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054079] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054096] fglrx_pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054101] fglrx_pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfea00000)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054107] fglrx_pci 0000:01:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xdc01)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054111] fglrx_pci 0000:01:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfe9f0004)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054115] fglrx_pci 0000:01:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xd000000c)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054119] fglrx_pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054123] fglrx_pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100403)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054154] HDA Intel 0000:01:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x205)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054166] HDA Intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xfe9ec004)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054169] HDA Intel 0000:01:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054173] HDA Intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054222] PM: early resume of devices complete after 0.694 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054224] acpi LNXIOBAY:00: parent PNP0A03:00 should not be sleeping
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054292]  pci0000:00: wake-up capability disabled by ACPI
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054296] e1000e 0000:00:19.0: PME# disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054339] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054383] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054387] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054406] usb usb3: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054422] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054426] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054443] usb usb4: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054456] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054460] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054485] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054488] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054511] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054534] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054538] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054555] usb usb5: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054568] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054572] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054589] usb usb6: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054603] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054607] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054624] usb usb7: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054637] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054641] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054665] pci 0000:00:1e.0: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054673] ahci 0000:00:1f.2: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054735] fglrx_pci 0000:01:00.0: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.057087] [fglrx] Power up the ASIC
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.057097] [fglrx] Preparing resume fglrx in kernel.
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066631] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066635] HDA Intel 0000:01:00.1: setting latency timer to 64
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066660] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066829] sd 2:0:0:0: [sda] Starting disk
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.075058] serial 00:06: activated
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.102383] [fglrx] Resuming fglrx in kernel completed.
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.102480] [fglrx] IRQ 46 Enabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208020] PM: resume of drv:usb dev:usb4 complete after 141.328 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208027] PM: resume of drv:hub dev:4-0:1.0 complete after 141.333 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208036] PM: resume of drv:usb dev:usb7 complete after 141.286 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208043] PM: resume of drv:hub dev:7-0:1.0 complete after 141.271 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208056] PM: resume of drv:usb dev:usb5 complete after 141.362 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208062] PM: resume of drv:hub dev:5-0:1.0 complete after 141.365 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312010] PM: resume of drv:usb dev:usb6 complete after 245.282 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312017] PM: resume of drv:hub dev:6-0:1.0 complete after 245.269 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312042] PM: resume of drv:usb dev:usb3 complete after 245.356 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312059] PM: resume of drv:hub dev:3-0:1.0 complete after 245.370 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312066] PM: resume of drv: dev:ep_81 complete after 196.012 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.337927] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 283.639 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.392017] ata4: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.400013] ata6: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.408018] ata1: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.450711] PM: resume of drv:HDA Intel dev:0000:00:1b.0 complete after 396.228 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.572008] usb 6-1: reset low speed USB device using uhci_hcd and address 2
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.612011] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.616273] ata2.00: configured for UDMA/100
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.879087] PM: resume of drv:usb dev:6-1 complete after 812.278 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.879093] PM: resume of drv:usbhid dev:6-1:1.0 complete after 812.275 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.120011] usb 3-2: reset low speed USB device using uhci_hcd and address 2
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427086] PM: resume of drv:usb dev:3-2 complete after 1360.301 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427093] PM: resume of drv:usbhid dev:3-2:1.0 complete after 1360.298 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427098] PM: resume of drv: dev:ep_81 complete after 1079.686 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.844010] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.855960] ata3.00: configured for UDMA/133
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892588] PM: resume of drv:sd dev:2:0:0:0 complete after 4825.757 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892596] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 4825.741 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892600] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 3465.470 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892627] PM: resume of devices complete after 4838.381 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892782] PM: resume devices took 4.840 seconds
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892815] PM: Finishing wakeup.
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Demoting known real-time threads.
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Successfully demoted thread 1619 of process 1608 (n/a).
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Successfully demoted thread 1618 of process 1608 (n/a).
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Successfully demoted thread 1611 of process 1608 (n/a).
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Successfully demoted thread 1608 of process 1608 (n/a).
Feb  6 10:15:16 OPlex-755 rtkit-daemon[1366]: Demoted 4 threads.
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892816] Restarting tasks ... done.
Feb  6 10:15:16 OPlex-755 acpid: client 1156[0:0] has disconnected
Feb  6 10:15:16 OPlex-755 acpid: client connected from 1156[0:0]
Feb  6 10:15:16 OPlex-755 acpid: 1 client rule loaded
Feb  6 10:15:16 OPlex-755 anacron[2652]: Anacron 2.3 started on 2011-02-06
Feb  6 10:15:16 OPlex-755 anacron[2652]: Normal exit (0 jobs run)
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> wake requested (sleeping: yes  enabled: yes)
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> waking up and re-enabling...
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> (eth0): now managed
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> (eth0): bringing up device.
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.052165] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.071076] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.256146] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> (eth0): preparing device.
Feb  6 10:15:16 OPlex-755 NetworkManager[987]: <info> (eth0): deactivating device (reason: 2).
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.312031] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.312232] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  6 10:15:17 OPlex-755 anacron[2822]: Anacron 2.3 started on 2011-02-06
Feb  6 10:15:17 OPlex-755 anacron[2822]: Normal exit (0 jobs run)
Feb  6 10:15:17 OPlex-755 kernel: [ 4899.840240] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Feb  6 10:15:17 OPlex-755 kernel: [ 4900.036890] EXT4-fs (sda6): re-mounted. Opts: commit=0
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> (eth0): carrier now ON (device state 2)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) starting connection 'Auto eth0'
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb  6 10:15:19 OPlex-755 NetworkManager[987]: <info> dhclient started with pid 2852
Feb  6 10:15:19 andFeb  6 10:16:47 OPlex-755 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb  6 10:16:47 OPlex-755 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="935" x-info="http://www.rsyslog.com"] (re)start
Feb  6 10:16:47 OPlex-755 rsyslogd: rsyslogd's groupid changed to 103
Feb  6 10:16:47 OPlex-755 rsyslogd: rsyslogd's userid changed to 101
Feb  6 10:16:47 OPlex-755 rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  6 10:16:47 OPlex-755 avahi-daemon[967]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Linux version 2.6.35-25-generic-pae (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 (Ubuntu 2.6.35-25.44-generic-pae 2.6.35.10)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdff800 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfdff800 - 00000000cfe53c00 (ACPI NVS)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfe53c00 - 00000000cfe55c00 (ACPI data)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfe55c00 - 00000000d0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000128000000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] NX (Execute Disable) protection: active
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] DMI 2.5 present.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] last_pfn = 0x128000 max_arch_pfn = 0x1000000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] MTRR default type: uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] MTRR fixed ranges enabled:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   00000-9FFFF write-back
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   A0000-BFFFF uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   C0000-D3FFF write-protect
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   D4000-EFFFF uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   F0000-FFFFF write-protect
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] MTRR variable ranges enabled:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   0 base 000000000 mask 000000000 write-back
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   1 base 0CFF00000 mask FFFF00000 uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   2 base 0D0000000 mask FF0000000 uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   4 disabled
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   5 disabled
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   6 disabled
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] e820 update range: 00000000cff00000 - 0000000100000000 (usable) ==> (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] modified physical RAM map:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfdff800 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000cfdff800 - 00000000cfe53c00 (ACPI NVS)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000cfe53c00 - 00000000cfe55c00 (ACPI data)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000cfe55c00 - 00000000d0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000100000000 - 0000000128000000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] initial memory mapped : 0 - 00e00000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] RAMDISK: 370c3000 - 37ff0000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Allocated new RAMDISK: 00a04000 - 0193048a
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Move RAMDISK from 00000000370c3000 - 0000000037fef489 to 00a04000 - 01930489
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: RSDP 000fec00 00024 (v02 DELL  )
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: XSDT 000fc59f 0008C (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: FACP 000fc6cf 000F4 (v03 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: DSDT fff78270 04596 (v01   DELL    dt_ex 00001000 INTL 20050624)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: FACS cfdff800 00040
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: SSDT fff7c925 000AA (v01   DELL    st_ex 00001000 INTL 20050624)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: APIC 000fc7c3 00092 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: BOOT 000fc855 00028 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: ASF! 000fc87d 00096 (v32 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: MCFG 000fc913 0003E (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: HPET 000fc951 00038 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: TCPA 000fcbad 00032 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: ____ 000fcbdf 00030 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: SLIC 000fc989 00176 (v01 DELL    B9K     00000015 ASL  00000061)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: SSDT cfdff840 001F9 (v01 DpgPmm  Cpu0Ist 00000011 INTL 20050624)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: SSDT cfdffc49 001F9 (v01 DpgPmm  Cpu1Ist 00000011 INTL 20050624)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: SSDT cfe00052 00140 (v01 DpgPmm    CpuPm 00000010 INTL 20050624)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] 3844MB HIGHMEM available.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] 891MB LOWMEM available.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   low ram: 0 - 37bfe000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Zone PFN ranges:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   HighMem  0x00037bfe -> 0x00128000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Movable zone start PFN for each node
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] early_node_map[4] active PFN ranges
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     0: 0x00000100 -> 0x000cfdff
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     0: 0x00100000 -> 0x00128000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] On node 0 totalpages: 1015182
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] free_area_init_node: node 0, pgdat c083ecc0, node_mem_map c1932020
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   HighMem zone: 7689 pages used for memmap
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   HighMem zone: 779256 pages, LIFO batch:31
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Using APIC driver default
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] nr_irqs_gsi: 40
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000f0000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:10000000)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] PERCPU: Embedded 15 pages/cpu @c4000000 s39872 r0 d21568 u262144
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] pcpu-alloc: s39872 r0 d21568 u262144 alloc=1*2097152
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1005709
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=c09c8086-30b9-48bb-8b6e-4942123202ae ro quiet splash
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing CPU#0
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] allocated 24248300 bytes of page_cgroup
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Subtract (59 early reservations)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #2 [0000100000 - 00009fb65c]   TEXT DATA BSS
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #3 [00009fc000 - 0000a03164]             BRK
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #4 [00000fe720 - 0000100000]   BIOS reserved
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #5 [00000fe710 - 00000fe720]    MP-table mpf
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #6 [000009ec00 - 00000f0000]   BIOS reserved
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #7 [00000f02b4 - 00000fe710]   BIOS reserved
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #8 [00000f0000 - 00000f02b4]    MP-table mpc
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #12 [0000a04000 - 0001931000]     NEW RAMDISK
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #13 [0001931000 - 0001932000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #14 [0001932000 - 0003e32000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #15 [0003e32000 - 0003e32004]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #16 [0003e32040 - 0003e32100]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #17 [0003e32100 - 0003e321a8]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #18 [0003e321c0 - 0003e351c0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #19 [0003e351c0 - 0003e35494]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #20 [0003e354c0 - 0003e414c0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #21 [0003e414c0 - 0003e414ed]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #22 [0003e41500 - 0003e4152f]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #23 [0003e41540 - 0003e4175c]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #24 [0003e41780 - 0003e417c0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #25 [0003e417c0 - 0003e41800]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #26 [0003e41800 - 0003e41840]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #27 [0003e41840 - 0003e41880]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #28 [0003e41880 - 0003e418c0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #29 [0003e418c0 - 0003e41900]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #30 [0003e41900 - 0003e41940]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #31 [0003e41940 - 0003e41980]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #32 [0003e41980 - 0003e419c0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #33 [0003e419c0 - 0003e41a00]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #34 [0003e41a00 - 0003e41a40]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #35 [0003e41a40 - 0003e41a80]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #36 [0003e41a80 - 0003e41a90]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #37 [0003e41ac0 - 0003e41ad0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #38 [0003e41b00 - 0003e41b6e]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #39 [0003e41b80 - 0003e41bee]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #40 [0004000000 - 000400f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #41 [0004040000 - 000404f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #42 [0004080000 - 000408f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #43 [00040c0000 - 00040cf000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #44 [0004100000 - 000410f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #45 [0004140000 - 000414f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #46 [0004180000 - 000418f000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #47 [00041c0000 - 00041cf000]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #48 [0003e43c00 - 0003e43c04]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #49 [0003e43c40 - 0003e43c44]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #50 [0003e43c80 - 0003e43ca0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #51 [0003e43cc0 - 0003e43ce0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #52 [0003e43d00 - 0003e43d90]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #53 [0003e43dc0 - 0003e43df0]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #54 [0003e43e00 - 0003e47e00]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #55 [0003e47e00 - 0003ec7e00]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #56 [0003ec7e00 - 0003f07e00]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #57 [0003e41c00 - 0003e41e40]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]   #58 [00041cf000 - 00058eefec]         BOOTMEM
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:00128000)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Memory: 3973024k/4849664k available (5090k kernel code, 87704k reserved, 2427k data, 708k init, 3147780k highmem)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] virtual kernel memory layout:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]       .init : 0xc0858000 - 0xc0909000   ( 708 kB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]       .data : 0xc05f8a1a - 0xc0857908   (2427 kB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05f8a1a   (5090 kB)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Hierarchical RCU implementation.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Console: colour VGA+ 80x25
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] console [tty0] enabled
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] hpet clockevent registered
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Fast TSC calibration using PIT
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Detected 2992.544 MHz processor.
Feb  6 10:16:47 OPlex-755 kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5985.08 BogoMIPS (lpj=11970176)
Feb  6 10:16:47 OPlex-755 kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Feb  6 10:16:47 OPlex-755 kernel: [    0.004023] Security Framework initialized
Feb  6 10:16:47 OPlex-755 kernel: [    0.004035] AppArmor: AppArmor initialized
Feb  6 10:16:47 OPlex-755 kernel: [    0.004036] Yama: becoming mindful.
Feb  6 10:16:47 OPlex-755 kernel: [    0.004077] Mount-cache hash table entries: 512
Feb  6 10:16:47 OPlex-755 kernel: [    0.004180] Initializing cgroup subsys ns
Feb  6 10:16:47 OPlex-755 kernel: [    0.004183] Initializing cgroup subsys cpuacct
Feb  6 10:16:47 OPlex-755 kernel: [    0.004187] Initializing cgroup subsys memory
Feb  6 10:16:47 OPlex-755 kernel: [    0.004193] Initializing cgroup subsys devices
Feb  6 10:16:47 OPlex-755 kernel: [    0.004195] Initializing cgroup subsys freezer
Feb  6 10:16:47 OPlex-755 kernel: [    0.004197] Initializing cgroup subsys net_cls
Feb  6 10:16:47 OPlex-755 kernel: [    0.004219] CPU: Physical Processor ID: 0
Feb  6 10:16:47 OPlex-755 avahi-daemon[967]: Successfully dropped root privileges.

---

### Post by ahoros on 2011-02-06
could it be possible that the problem is with audio - pulse 
: Feb  6 10:15:41 OPlex-755 pulseaudio[1608]: ratelimit.c: 658 events suppressed

..... I do find pulse audio not reliable enough - there are problems when playing video files etc.



MESSAGES:
Feb  6 08:48:33 OPlex-755 kernel: [   21.267609] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Feb  6 10:09:29 OPlex-755 kernel: [ 4891.294672] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Feb  6 10:09:29 OPlex-755 kernel: [ 4891.297825] EXT4-fs (sda6): re-mounted. Opts: commit=0
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.209826] PM: Syncing filesystems ... done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.210588] Freezing user space processes ... (elapsed 0.01 seconds) done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.224262] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.240285] Suspending console(s) (use no_console_suspend to debug)
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.240579] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242192] serial 00:06: disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242279] [fglrx] IRQ 46 Disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242310] [fglrx] Preparing suspend fglrx in kernel.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242314] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242331] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242357] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242966] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.242972] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246433] e1000e 0000:00:19.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.246452]  pci0000:00: wake-up capability enabled by ACPI
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.256285] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.260284] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344643] HDA Intel 0000:00:1b.0: PCI INT A disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.344715] HDA Intel 0000:01:00.1: PCI INT B disabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.360256] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.873 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.360261] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 118.051 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.361897] sd 2:0:0:0: [sda] Stopping disk
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632898] PM: suspend of drv:sd dev:2:0:0:0 complete after 392.323 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632903] PM: suspend of drv:scsi dev:target2:0:0 complete after 392.293 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.632908] PM: suspend of drv:scsi dev:host2 complete after 392.249 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658159] [fglrx] Suspending fglrx in kernel completed.
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658162] [fglrx] Power down the ASIC .
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658198] PM: suspend of drv:fglrx_pci dev:0000:01:00.0 complete after 415.967 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.658220] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 411.716 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744009] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 501.741 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744018] PM: suspend of drv: dev:pci0000:00 complete after 497.497 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744025] PM: suspend of devices complete after 503.519 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.744027] PM: suspend devices took 0.504 seconds
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.776092] PM: late suspend of devices complete after 32.061 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.776929] ACPI: Preparing to enter system sleep state S3
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.778430] PM: Saving platform NVS memory
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.785214] Disabling non-boot CPUs ...
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.788355] Broke affinity for irq 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.788363] Broke affinity for irq 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.892016] CPU 1 is now offline
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.892019] SMP alternatives: switching to UP code
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] PM: Restoring platform NVS memory
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] Enabling non-boot CPUs ...
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897303] SMP alternatives: switching to SMP code
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.902325] Booting Node 0 Processor 1 APIC 0x1
Feb  6 10:15:16 OPlex-755 kernel: [ 4893.897044] Initializing CPU#1
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.032257] CPU1 is up
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.033093] ACPI: Waking up from system sleep state S3
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.038243] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1 - docking
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054222] PM: early resume of devices complete after 0.694 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054224] acpi LNXIOBAY:00: parent PNP0A03:00 should not be sleeping
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054292]  pci0000:00: wake-up capability disabled by ACPI
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054383] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054406] usb usb3: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054422] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054443] usb usb4: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054456] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054485] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054534] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054555] usb usb5: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054568] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054589] usb usb6: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054603] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054624] usb usb7: root hub lost power or was reset
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.054637] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.057087] [fglrx] Power up the ASIC
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.057097] [fglrx] Preparing resume fglrx in kernel.
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066631] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.066829] sd 2:0:0:0: [sda] Starting disk
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.075058] serial 00:06: activated
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.102383] [fglrx] Resuming fglrx in kernel completed.
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.102480] [fglrx] IRQ 46 Enabled
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208020] PM: resume of drv:usb dev:usb4 complete after 141.328 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208027] PM: resume of drv:hub dev:4-0:1.0 complete after 141.333 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208036] PM: resume of drv:usb dev:usb7 complete after 141.286 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208043] PM: resume of drv:hub dev:7-0:1.0 complete after 141.271 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208056] PM: resume of drv:usb dev:usb5 complete after 141.362 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.208062] PM: resume of drv:hub dev:5-0:1.0 complete after 141.365 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312010] PM: resume of drv:usb dev:usb6 complete after 245.282 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312017] PM: resume of drv:hub dev:6-0:1.0 complete after 245.269 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312042] PM: resume of drv:usb dev:usb3 complete after 245.356 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312059] PM: resume of drv:hub dev:3-0:1.0 complete after 245.370 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.312066] PM: resume of drv: dev:ep_81 complete after 196.012 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.337927] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 283.639 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.392017] ata4: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.400013] ata6: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.408018] ata1: SATA link down (SStatus 4 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.450711] PM: resume of drv:HDA Intel dev:0000:00:1b.0 complete after 396.228 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.572008] usb 6-1: reset low speed USB device using uhci_hcd and address 2
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.612011] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.616273] ata2.00: configured for UDMA/100
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.879087] PM: resume of drv:usb dev:6-1 complete after 812.278 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4894.879093] PM: resume of drv:usbhid dev:6-1:1.0 complete after 812.275 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.120011] usb 3-2: reset low speed USB device using uhci_hcd and address 2
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427086] PM: resume of drv:usb dev:3-2 complete after 1360.301 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427093] PM: resume of drv:usbhid dev:3-2:1.0 complete after 1360.298 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4895.427098] PM: resume of drv: dev:ep_81 complete after 1079.686 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.844010] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.855960] ata3.00: configured for UDMA/133
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892588] PM: resume of drv:sd dev:2:0:0:0 complete after 4825.757 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892596] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 4825.741 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892600] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 3465.470 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892627] PM: resume of devices complete after 4838.381 msecs
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892782] PM: resume devices took 4.840 seconds
Feb  6 10:15:16 OPlex-755 kernel: [ 4898.892816] Restarting tasks ... done.
Feb  6 10:15:16 OPlex-755 kernel: [ 4899.312232] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  6 10:15:17 OPlex-755 kernel: [ 4899.840240] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Feb  6 10:15:17 OPlex-755 kernel: [ 4900.036890] EXT4-fs (sda6): re-mounted. Opts: commit=0
Feb  6 10:15:19 OPlex-755 kernel: [ 4901.820859] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Feb  6 10:15:19 OPlex-755 kernel: [ 4901.821066] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb  6 10:15:24 OPlex-755 gnome-screensaver-dialog: pam_sm_authenticate: Called
Feb  6 10:15:24 OPlex-755 gnome-screensaver-dialog: pam_sm_authenticate: username = [gosc]
Feb  6 10:15:41 OPlex-755 pulseaudio[1608]: ratelimit.c: 658 events suppressed
Feb  6 10:16:47 OPlex-755 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb  6 10:16:47 OPlex-755 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="935" x-info="http://www.rsyslog.com"] (re)start
Feb  6 10:16:47 OPlex-755 rsyslogd: rsyslogd's groupid changed to 103
Feb  6 10:16:47 OPlex-755 rsyslogd: rsyslogd's userid changed to 101
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Linux version 2.6.35-25-generic-pae (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 (Ubuntu 2.6.35-25.44-generic-pae 2.6.35.10)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdff800 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfdff800 - 00000000cfe53c00 (ACPI NVS)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfe53c00 - 00000000cfe55c00 (ACPI data)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000cfe55c00 - 00000000d0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000128000000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] NX (Execute Disable) protection: active
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] DMI 2.5 present.
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] last_pfn = 0x128000 max_arch_pfn = 0x1000000
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000] modified physical RAM map:
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Feb  6 10:16:47 OPlex-755 kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfdff800 (usable)



P.S. I attach logs

---

### Post by quequotion on 2012-01-18
This occasionally happens to me as well.

I've been experiencing sudden, somewhat random reboots, particularly at times of high CPU usage.

The standby and shutdown scripts can be intensive and I think that's why it triggers a reboot.

In my case the reboots usually happen while using the computer and occasionally while shutting down or suspending.

---

