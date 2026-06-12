---
title: "Sudden reboots and shutdowns"
date: 2009-04-15
forum: General Help
---

### Post by frecon on 2009-04-15
A few times the past few weeks Ubuntu have been rebooting or shut down the computer without me doing it. I can't find a common factor for what is causing the sudden reboots and shutdowns. Sometimes it have happen when I've been surfing the net, sometimes when doing something else. Is there a way to check what's actually going on here? Is there a system log that I can check for abnormalities?

Thanks in advance for your reply.

---

### Post by Alekz_ on 2009-04-15
Sure you have! :)

These files may help you:
/var/log/syslog
/var/log/messages

and you help the dmesg command too! 

[]'s

Alekz_

---

### Post by sahabcse on 2009-04-15
last -i

---

### Post by frecon on 2009-04-22
Thanks for your replies. Just the recently I had one crash. When I went through the logs there seem to be something wrong with the audio. Or am I wrong? Can I do something about it?


last -i
```
frecon@frecon-laptop:/var/log$ last -i
frecon     pts/0        0.0.0.0          Wed Apr 22 18:14   still logged in   
frecon     tty7         0.0.0.0          Wed Apr 22 18:10   still logged in   
reboot   system boot  0.0.0.0          Wed Apr 22 18:09 - 18:22  (00:13)    
frecon     tty7         0.0.0.0          Wed Apr 22 18:05 - crash  (00:04)    
reboot   system boot  0.0.0.0          Wed Apr 22 17:56 - 18:22  (00:25)    
frecon     pts/0        0.0.0.0          Tue Apr 21 22:52 - 23:14  (00:22)    
frecon     tty7         0.0.0.0          Tue Apr 21 22:38 - 23:29  (00:51)    
reboot   system boot  0.0.0.0          Tue Apr 21 22:35 - 23:29  (00:54)    
frecon     tty7         0.0.0.0          Tue Apr 21 08:42 - 09:43  (01:00)    
reboot   system boot  0.0.0.0          Tue Apr 21 08:39 - 09:43  (01:04)    
frecon     tty7         0.0.0.0          Mon Apr 20 22:35 - 00:00  (01:24)    
reboot   system boot  0.0.0.0          Mon Apr 20 22:33 - 00:00  (01:26)    
frecon     tty7         0.0.0.0          Mon Apr 20 18:01 - 18:21  (00:19)    
reboot   system boot  0.0.0.0          Mon Apr 20 17:45 - 18:21  (00:35)    
frecon     tty7         0.0.0.0          Mon Apr 20 16:02 - crash  (01:42)    
reboot   system boot  0.0.0.0          Mon Apr 20 16:01 - 18:21  (02:20)    
frecon     pts/0        0.0.0.0          Sun Apr 19 23:11 - down   (00:00)    
frecon     pts/0        0.0.0.0          Sun Apr 19 14:08 - 23:09  (09:01)    
frecon     pts/1        0.0.0.0          Sun Apr 19 14:03 - 14:04  (00:01)    
frecon     pts/0        0.0.0.0          Sun Apr 19 14:02 - 14:07  (00:05)    
frecon     tty7         0.0.0.0          Sun Apr 19 13:44 - down   (09:27)    
reboot   system boot  0.0.0.0          Sun Apr 19 13:42 - 23:11  (09:29)    
frecon     pts/0        0.0.0.0          Sun Apr 19 11:25 - down   (01:02)    
frecon     tty7         0.0.0.0          Sun Apr 19 11:24 - 12:28  (01:03)    
marie    tty7         0.0.0.0          Sun Apr 19 11:18 - 11:23  (00:05)    
reboot   system boot  0.0.0.0          Sun Apr 19 11:17 - 12:28  (01:11)    
frecon     tty7         0.0.0.0          Sat Apr 18 21:20 - 23:26  (02:06)    
reboot   system boot  0.0.0.0          Sat Apr 18 21:14 - 23:26  (02:12)    
frecon     pts/0        0.0.0.0          Sat Apr 18 21:13 - crash  (00:01)    
frecon     pts/0        0.0.0.0          Sat Apr 18 21:01 - 21:12  (00:11)    
frecon     tty7         0.0.0.0          Sat Apr 18 20:59 - crash  (00:15)    
reboot   system boot  0.0.0.0          Sat Apr 18 20:54 - 23:26  (02:32)    
frecon     tty7         0.0.0.0          Sat Apr 18 18:30 - crash  (02:24)    
reboot   system boot  0.0.0.0          Sat Apr 18 18:29 - 23:26  (04:57)    
frecon     pts/0        0.0.0.0          Sat Apr 18 12:20 - 14:54  (02:33)    
frecon     tty7         0.0.0.0          Sat Apr 18 11:32 - 16:07  (04:34)    
r
```

/var/log/messages
```
Apr 22 18:05:04 frecon-laptop kernel: [  515.048206] usb 7-2: new high speed USB device using ehci_hcd and address 9
Apr 22 18:05:04 frecon-laptop kernel: [  515.187042] usb 7-2: configuration #1 chosen from 1 choice
Apr 22 18:05:04 frecon-laptop kernel: [  515.268238] usbcore: registered new interface driver libusual
Apr 22 18:05:04 frecon-laptop kernel: [  515.281748] Initializing USB Mass Storage driver...
Apr 22 18:05:04 frecon-laptop kernel: [  515.283854] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 22 18:05:04 frecon-laptop kernel: [  515.285760] usbcore: registered new interface driver usb-storage
Apr 22 18:05:04 frecon-laptop kernel: [  515.285771] USB Mass Storage support registered.
Apr 22 18:05:09 frecon-laptop kernel: [  520.285883] scsi 5:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
Apr 22 18:05:09 frecon-laptop kernel: [  520.287688] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 18:05:09 frecon-laptop kernel: [  520.288816] sd 5:0:0:0: [sdb] Write Protect is off
Apr 22 18:05:09 frecon-laptop kernel: [  520.290691] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 18:05:09 frecon-laptop kernel: [  520.291690] sd 5:0:0:0: [sdb] Write Protect is off
Apr 22 18:05:10 frecon-laptop kernel: [  520.292821]  sdb: sdb1
Apr 22 18:05:10 frecon-laptop kernel: [  520.334047] sd 5:0:0:0: [sdb] Attached SCSI disk
Apr 22 18:05:10 frecon-laptop kernel: [  520.334643] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 22 18:05:13 frecon-laptop pulseaudio[7012]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 22 18:05:13 frecon-laptop pulseaudio[7014]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operationen inte tillåten
Apr 22 18:05:13 frecon-laptop pulseaudio[7014]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operationen inte tillåten
Apr 22 18:05:51 frecon-laptop kernel: [  561.388325] UDF-fs: No VRS found
Apr 22 18:09:38 frecon-laptop syslogd 1.5.0#2ubuntu6: restart.
Apr 22 18:09:38 frecon-laptop kernel: Inspecting /boot/System.map-2.6.27-13-generic
```

/var/log/syslog```
Apr 22 18:05:04 frecon-laptop kernel: [  515.048206] usb 7-2: new high speed USB device using ehci_hcd and address 9
Apr 22 18:05:04 frecon-laptop kernel: [  515.187042] usb 7-2: configuration #1 chosen from 1 choice
Apr 22 18:05:04 frecon-laptop kernel: [  515.268238] usbcore: registered new interface driver libusual
Apr 22 18:05:04 frecon-laptop kernel: [  515.281748] Initializing USB Mass Storage driver...
Apr 22 18:05:04 frecon-laptop kernel: [  515.283854] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 22 18:05:04 frecon-laptop kernel: [  515.285723] usb-storage: device found at 9
Apr 22 18:05:04 frecon-laptop kernel: [  515.285735] usb-storage: waiting for device to settle before scanning
Apr 22 18:05:04 frecon-laptop kernel: [  515.285760] usbcore: registered new interface driver usb-storage
Apr 22 18:05:04 frecon-laptop kernel: [  515.285771] USB Mass Storage support registered.
Apr 22 18:05:09 frecon-laptop kernel: [  520.284680] usb-storage: device scan complete
Apr 22 18:05:09 frecon-laptop kernel: [  520.285883] scsi 5:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
Apr 22 18:05:09 frecon-laptop kernel: [  520.287688] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 18:05:09 frecon-laptop kernel: [  520.288816] sd 5:0:0:0: [sdb] Write Protect is off
Apr 22 18:05:09 frecon-laptop kernel: [  520.288826] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
Apr 22 18:05:09 frecon-laptop kernel: [  520.288833] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Apr 22 18:05:09 frecon-laptop kernel: [  520.290691] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Apr 22 18:05:09 frecon-laptop kernel: [  520.291690] sd 5:0:0:0: [sdb] Write Protect is off
Apr 22 18:05:09 frecon-laptop kernel: [  520.291700] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
Apr 22 18:05:09 frecon-laptop kernel: [  520.291706] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Apr 22 18:05:10 frecon-laptop kernel: [  520.292821]  sdb: sdb1
Apr 22 18:05:10 frecon-laptop kernel: [  520.334047] sd 5:0:0:0: [sdb] Attached SCSI disk
Apr 22 18:05:10 frecon-laptop kernel: [  520.334643] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 22 18:05:13 frecon-laptop pulseaudio[7012]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 22 18:05:13 frecon-laptop pulseaudio[7014]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operationen inte tillåten
Apr 22 18:05:13 frecon-laptop pulseaudio[7014]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operationen inte tillåten
Apr 22 18:05:30 frecon-laptop x-session-manager[6947]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Apr 22 18:05:31 frecon-laptop pulseaudio[7014]: module-x11-xsmp.c: X11 session manager not running.
Apr 22 18:05:31 frecon-laptop pulseaudio[7014]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Apr 22 18:05:42 frecon-laptop kernel: [  552.825445] CPU0 attaching NULL sched-domain.
Apr 22 18:05:42 frecon-laptop kernel: [  552.825453] CPU1 attaching NULL sched-domain.
Apr 22 18:05:42 frecon-laptop kernel: [  552.865134] CPU0 attaching sched-domain:
Apr 22 18:05:42 frecon-laptop kernel: [  552.865140]  domain 0: span 0-1 level MC
Apr 22 18:05:43 frecon-laptop kernel: [  552.865142]   groups: 0 1
Apr 22 18:05:43 frecon-laptop kernel: [  552.865148] CPU1 attaching sched-domain:
Apr 22 18:05:43 frecon-laptop kernel: [  552.865150]  domain 0: span 0-1 level MC
Apr 22 18:05:43 frecon-laptop kernel: [  552.865152]   groups: 1 0
Apr 22 18:05:43 frecon-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto cojan' 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto cojan' requires no security.  No secrets needed. 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Config: added 'ssid' value 'cojan' 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 22 18:05:46 frecon-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Apr 22 18:05:50 frecon-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 22 18:05:50 frecon-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Apr 22 18:05:50 frecon-laptop kernel: [  561.184230] wlan0: authenticate with AP 00:13:46:c8:72:4a
Apr 22 18:05:50 frecon-laptop kernel: [  561.199852] wlan0: authenticated
Apr 22 18:05:50 frecon-laptop kernel: [  561.199868] wlan0: associate with AP 00:13:46:c8:72:4a
Apr 22 18:05:50 frecon-laptop kernel: [  561.201587] wlan0: RX AssocResp from 00:13:46:c8:72:4a (capab=0x441 status=12 aid=1)
Apr 22 18:05:50 frecon-laptop kernel: [  561.201596] wlan0: AP denied association (code=12)
Apr 22 18:05:51 frecon-laptop kernel: [  561.388325] UDF-fs: No VRS found
Apr 22 18:05:51 frecon-laptop kernel: [  561.396096] wlan0: associate with AP 00:13:46:c8:72:4a
Apr 22 18:05:51 frecon-laptop kernel: [  561.398606] wlan0: RX AssocResp from 00:13:46:c8:72:4a (capab=0x461 status=0 aid=1)
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'cojan'. 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 22 18:05:51 frecon-laptop kernel: [  561.398616] wlan0: associated
Apr 22 18:05:51 frecon-laptop kernel: [  561.406270] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr 22 18:05:51 frecon-laptop kernel: [  561.407562] ISOFS: changing to secondary root
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  dhclient started with pid 7350 
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 22 18:05:51 frecon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 22 18:05:51 frecon-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 22 18:05:51 frecon-laptop dhclient: All rights reserved.
Apr 22 18:05:51 frecon-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 22 18:05:51 frecon-laptop dhclient: 
Apr 22 18:05:51 frecon-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 22 18:05:51 frecon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Apr 22 18:05:51 frecon-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 22 18:05:51 frecon-laptop dhclient: Listening on LPF/wlan0/00:1c:bf:51:32:df
Apr 22 18:05:51 frecon-laptop dhclient: Sending on   LPF/wlan0/00:1c:bf:51:32:df
Apr 22 18:05:51 frecon-laptop dhclient: Sending on   Socket/fallback
Apr 22 18:05:54 frecon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 22 18:05:54 frecon-laptop dhclient: DHCPOFFER of 192.168.0.101 from 192.168.0.1
Apr 22 18:05:54 frecon-laptop dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
Apr 22 18:05:59 frecon-laptop dhclient: DHCPACK of 192.168.0.101 from 192.168.0.1
Apr 22 18:05:59 frecon-laptop dhclient: bound to 192.168.0.101 -- renewal in 270353 seconds.
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>    address 192.168.0.101 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>    gateway 192.168.0.1 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>    nameserver '192.168.0.1' 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>    domain name 'skycom.se' 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 22 18:05:59 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 22 18:05:59 frecon-laptop avahi-daemon[5300]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Apr 22 18:05:59 frecon-laptop avahi-daemon[5300]: New relevant interface wlan0.IPv4 for mDNS.
Apr 22 18:05:59 frecon-laptop avahi-daemon[5300]: Registering new address record for 192.168.0.101 on wlan0.IPv4.
Apr 22 18:06:00 frecon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Apr 22 18:06:00 frecon-laptop NetworkManager: <info>  Policy set 'Auto cojan' (wlan0) as default for routing and DNS. 
Apr 22 18:06:00 frecon-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr 22 18:06:00 frecon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 22 18:06:00 frecon-laptop postfix/master[5987]: reload configuration /etc/postfix
Apr 22 18:06:01 frecon-laptop ntpdate[7443]: adjust time server 91.189.94.4 offset 0.422283 sec
Apr 22 18:09:38 frecon-laptop syslogd 1.5.0#2ubuntu6: restart.
```

/var/log/dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-13-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Thu Feb 26 07:26:43 UTC 2009 (Ubuntu 2.6.27-13.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe6d800 (usable)
[    0.000000]  BIOS-e820: 000000007fe6d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fe6d max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782b000 - 37fefc45
[    0.000000] ACPI: RSDP 000FBC00, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7FE6F200, 005C (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: FACP 7FE6F09C, 00F4 (r4 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: DSDT 7FE6F800, 5733 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FE7E000, 0040
[    0.000000] ACPI: HPET 7FE6F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7FE6F400, 0068 (r1 DELL    M08     27D80C1A ASL        47)
[    0.000000] ACPI: MCFG 7FE6F3C0, 003E (r16 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: SLIC 7FE6F49C, 0176 (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: BOOT 7FE6EFC0, 0028 (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: SSDT 7FE6D9BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [003782b000 - 0037fefc45]          RAMDISK ==> [003782b000 - 0037fefc45]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fe6d
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe6d
[    0.000000] On node 0 totalpages: 523788
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 291920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519183
[    0.000000] Kernel command line: root=UUID=f1ef7b10-115f-416c-9ad6-e94317584ecf ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.986 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062048k/2095540k available (2577k kernel code, 32228k reserved, 1163k data, 428k init, 1178036k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc038478a - 0xc04a7680   (1163 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038478a   (2577 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.97 BogoMIPS (lpj=7979944)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017836] ACPI: Core revision 20080609
[    0.019802] ACPI: Checking initramfs for custom DSDT
[    0.354450] ENABLING IO-APIC IRQs
[    0.354641] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.394341] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.396024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.98 BogoMIPS (lpj=7979968)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.480500] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.480517] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.484048] Brought up 2 CPUs
[    0.484051] Total of 2 processors activated (7979.95 BogoMIPS).
[    0.484073] CPU0 attaching sched-domain:
[    0.484076]  domain 0: span 0-1 level MC
[    0.484078]   groups: 0 1
[    0.484085] CPU1 attaching sched-domain:
[    0.484087]  domain 0: span 0-1 level MC
[    0.484089]   groups: 1 0
[    0.484163] net_namespace: 840 bytes
[    0.484163] Booting paravirtualized kernel on bare hardware
[    0.484299] Time: 18:09:06  Date: 04/22/09
[    0.484324] NET: Registered protocol family 16
[    0.484342] EISA bus registered
[    0.484342] ACPI: bus type pci registered
[    0.484342] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.484342] PCI: MCFG area at f8000000 reserved in E820
[    0.484342] PCI: Using MMCONFIG for extended config space
[    0.484342] PCI: Using configuration type 1 for base access
[    0.484978] ACPI: EC: Look up EC in DSDT
[    0.500320] ACPI: SSDT 7FE7E080, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.518321] ACPI: Interpreter enabled
[    0.518326] ACPI: (supports S0 S3 S4 S5)
[    0.520229] ACPI: Using IOAPIC for interrupt routing
[    0.568211] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.568211] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.568211] pci 0000:00:01.0: PME# disabled
[    0.568223] PCI: 0000:00:1a.0 reg 20 io port: [6f20, 6f3f]
[    0.568296] PCI: 0000:00:1a.1 reg 20 io port: [6f00, 6f1f]
[    0.568373] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fed1c400, fed1c7ff]
[    0.568454] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.568460] pci 0000:00:1a.7: PME# disabled
[    0.568509] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f6ffc000, f6ffffff]
[    0.568590] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.568595] pci 0000:00:1b.0: PME# disabled
[    0.568691] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.568697] pci 0000:00:1c.0: PME# disabled
[    0.568792] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.568798] pci 0000:00:1c.1: PME# disabled
[    0.568895] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.568901] pci 0000:00:1c.3: PME# disabled
[    0.568998] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.569004] pci 0000:00:1c.5: PME# disabled
[    0.569054] PCI: 0000:00:1d.0 reg 20 io port: [6f80, 6f9f]
[    0.569124] PCI: 0000:00:1d.1 reg 20 io port: [6f60, 6f7f]
[    0.569194] PCI: 0000:00:1d.2 reg 20 io port: [6f40, 6f5f]
[    0.569269] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fed1c000, fed1c3ff]
[    0.569349] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.569355] pci 0000:00:1d.7: PME# disabled
[    0.569534] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.569539] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.569587] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.569595] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.569603] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.569612] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.569620] PCI: 0000:00:1f.1 reg 20 io port: [6fa0, 6faf]
[    0.569700] PCI: 0000:00:1f.2 reg 10 io port: [6eb0, 6eb7]
[    0.569708] PCI: 0000:00:1f.2 reg 14 io port: [6eb8, 6ebb]
[    0.569716] PCI: 0000:00:1f.2 reg 18 io port: [6ec0, 6ec7]
[    0.569725] PCI: 0000:00:1f.2 reg 1c io port: [6ec8, 6ecb]
[    0.569733] PCI: 0000:00:1f.2 reg 20 io port: [6ee0, 6eff]
[    0.569741] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f6ffb800, f6ffbfff]
[    0.569802] pci 0000:00:1f.2: PME# supported from D3hot
[    0.569807] pci 0000:00:1f.2: PME# disabled
[    0.569829] PCI: 0000:00:1f.3 reg 10 32bit mmio: [f6ffb700, f6ffb7ff]
[    0.569856] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.569940] PCI: 0000:01:00.0 reg 10 32bit mmio: [f5000000, f5ffffff]
[    0.569957] PCI: 0000:01:00.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.569974] PCI: 0000:01:00.0 reg 1c 64bit mmio: [f2000000, f3ffffff]
[    0.569983] PCI: 0000:01:00.0 reg 24 io port: [ef00, ef7f]
[    0.569992] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.570100] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.570104] PCI: bridge 0000:00:01.0 32bit mmio: [f2000000, f6efffff]
[    0.570109] PCI: bridge 0000:00:01.0 64bit mmio pref: [e0000000, efffffff]
[    0.570369] PCI: 0000:0c:00.0 reg 10 32bit mmio: [f1fff000, f1ffffff]
[    0.570663] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.570676] pci 0000:0c:00.0: PME# disabled
[    0.570735] PCI: bridge 0000:00:1c.1 32bit mmio: [f1f00000, f1ffffff]
[    0.570805] PCI: bridge 0000:00:1c.3 io port: [d000, dfff]
[    0.570811] PCI: bridge 0000:00:1c.3 32bit mmio: [f1c00000, f1efffff]
[    0.570819] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0000000, f01fffff]
[    0.571014] PCI: 0000:09:00.0 reg 10 64bit mmio: [f1bf0000, f1bfffff]
[    0.571285] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.571297] pci 0000:09:00.0: PME# disabled
[    0.571356] PCI: bridge 0000:00:1c.5 32bit mmio: [f1b00000, f1bfffff]
[    0.571412] PCI: 0000:03:01.0 reg 10 32bit mmio: [f1aff800, f1afffff]
[    0.572033] pci 0000:03:01.0: supports D1
[    0.572035] pci 0000:03:01.0: supports D2
[    0.572037] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.572042] pci 0000:03:01.0: PME# disabled
[    0.572082] PCI: 0000:03:01.1 reg 10 32bit mmio: [f1aff500, f1aff5ff]
[    0.572156] pci 0000:03:01.1: supports D1
[    0.572157] pci 0000:03:01.1: supports D2
[    0.572159] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.572165] pci 0000:03:01.1: PME# disabled
[    0.572204] PCI: 0000:03:01.2 reg 10 32bit mmio: [f1aff600, f1aff6ff]
[    0.572277] pci 0000:03:01.2: supports D1
[    0.572278] pci 0000:03:01.2: supports D2
[    0.572280] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.572286] pci 0000:03:01.2: PME# disabled
[    0.572325] PCI: 0000:03:01.3 reg 10 32bit mmio: [f1aff700, f1aff7ff]
[    0.572397] pci 0000:03:01.3: supports D1
[    0.572399] pci 0000:03:01.3: supports D2
[    0.572401] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.572407] pci 0000:03:01.3: PME# disabled
[    0.572474] pci 0000:00:1e.0: transparent bridge
[    0.572483] PCI: bridge 0000:00:1e.0 32bit mmio: [f1a00000, f1afffff]
[    0.572528] bus 00 -> node 0
[    0.572535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.573072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.573255] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.573380] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.573530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.573680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.573827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.588178] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.588330] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.588480] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.588629] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.588779] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.588932] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.589084] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.589221] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.589304] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.589304] pnp: PnP ACPI init
[    0.589304] ACPI: bus type pnp registered
[    0.612408] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.612411] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.612458] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.612458] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.612458] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.612458] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.640234] pnp: PnP ACPI: found 12 devices
[    0.640237] ACPI: ACPI bus type pnp unregistered
[    0.640240] PnPBIOS: Disabled by ACPI PNP
[    0.640256] PCI: Using ACPI for IRQ routing
[    0.648040] NET: Registered protocol family 8
[    0.648042] NET: Registered protocol family 20
[    0.648058] NetLabel: Initializing
[    0.648058] NetLabel:  domain hash size = 128
[    0.648058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.648063] NetLabel:  unlabeled traffic allowed by default
[    0.648071] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.648076] hpet0: 3 64-bit timers, 14318180 Hz
[    0.649554] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.649557]    actual entries 65620
[    0.649645] AppArmor: AppArmor Filesystem Enabled
[    0.649671] ACPI: RTC can wake from S4
[    0.652040] Switched to high resolution mode on CPU 0
[    0.652534] Switched to high resolution mode on CPU 1
[    0.656024] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.656032] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.656038] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.656041] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.656048] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.656051] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.656054] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.656056] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.656063] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.656066] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.656069] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.656072] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.656075] system 00:0b: iomem range 0x100000-0x7fe6d7ff could not be reserved
[    0.656078] system 00:0b: iomem range 0x7fe6d800-0x7fefffff could not be reserved
[    0.656081] system 00:0b: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    0.656084] system 00:0b: iomem range 0x7ff00000-0x806fffff could not be reserved
[    0.656087] system 00:0b: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.656090] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.656093] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.656096] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.656099] system 00:0b: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.656102] system 00:0b: iomem range 0xfeda0000-0xfeda3fff could not be reserved
[    0.656106] system 00:0b: iomem range 0xfeda4000-0xfeda4fff could not be reserved
[    0.656109] system 00:0b: iomem range 0xfeda5000-0xfeda5fff could not be reserved
[    0.656112] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.656115] system 00:0b: iomem range 0xfed18000-0xfed1bfff could not be reserved
[    0.656118] system 00:0b: iomem range 0xf8000000-0xfbffffff could not be reserved
[    0.691214] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.691217] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.691221] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
[    0.691225] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.691230] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.691233] pci 0000:00:1c.0:   IO window: disabled
[    0.691239] pci 0000:00:1c.0:   MEM window: disabled
[    0.691244] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.691252] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.691255] pci 0000:00:1c.1:   IO window: disabled
[    0.691261] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
[    0.691266] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.691275] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.691279] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.691285] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
[    0.691291] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.691299] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.691301] pci 0000:00:1c.5:   IO window: disabled
[    0.691308] pci 0000:00:1c.5:   MEM window: 0xf1b00000-0xf1bfffff
[    0.691313] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.691322] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.691324] pci 0000:00:1e.0:   IO window: disabled
[    0.691330] pci 0000:00:1e.0:   MEM window: 0xf1a00000-0xf1afffff
[    0.691336] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.691351] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.691356] pci 0000:00:01.0: setting latency timer to 64
[    0.691364] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.691370] pci 0000:00:1c.0: setting latency timer to 64
[    0.691380] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.691386] pci 0000:00:1c.1: setting latency timer to 64
[    0.691396] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.691401] pci 0000:00:1c.3: setting latency timer to 64
[    0.691411] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.691416] pci 0000:00:1c.5: setting latency timer to 64
[    0.691425] pci 0000:00:1e.0: setting latency timer to 64
[    0.691430] bus: 00 index 0 io port: [0, ffff]
[    0.691432] bus: 00 index 1 mmio: [0, ffffffff]
[    0.691434] bus: 01 index 0 io port: [e000, efff]
[    0.691436] bus: 01 index 1 mmio: [f2000000, f6efffff]
[    0.691438] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.691440] bus: 01 index 3 mmio: [0, 0]
[    0.691442] bus: 0b index 0 mmio: [0, 0]
[    0.691444] bus: 0b index 1 mmio: [0, 0]
[    0.691446] bus: 0b index 2 mmio: [0, 0]
[    0.691448] bus: 0b index 3 mmio: [0, 0]
[    0.691450] bus: 0c index 0 mmio: [0, 0]
[    0.691452] bus: 0c index 1 mmio: [f1f00000, f1ffffff]
[    0.691454] bus: 0c index 2 mmio: [0, 0]
[    0.691456] bus: 0c index 3 mmio: [0, 0]
[    0.691458] bus: 0d index 0 io port: [d000, dfff]
[    0.691460] bus: 0d index 1 mmio: [f1c00000, f1efffff]
[    0.691462] bus: 0d index 2 mmio: [f0000000, f01fffff]
[    0.691464] bus: 0d index 3 mmio: [0, 0]
[    0.691466] bus: 09 index 0 mmio: [0, 0]
[    0.691468] bus: 09 index 1 mmio: [f1b00000, f1bfffff]
[    0.691470] bus: 09 index 2 mmio: [0, 0]
[    0.691472] bus: 09 index 3 mmio: [0, 0]
[    0.691474] bus: 03 index 0 mmio: [0, 0]
[    0.691476] bus: 03 index 1 mmio: [f1a00000, f1afffff]
[    0.691478] bus: 03 index 2 mmio: [0, 0]
[    0.691480] bus: 03 index 3 io port: [0, ffff]
[    0.691483] bus: 03 index 4 mmio: [0, ffffffff]
[    0.691491] NET: Registered protocol family 2
[    0.704048] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.704272] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.704622] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.704800] TCP: Hash tables configured (established 131072 bind 65536)
[    0.704803] TCP reno registered
[    0.708071] NET: Registered protocol family 1
[    0.708180] checking if image is initramfs... it is
[    1.388164] Freeing initrd memory: 7955k freed
[    1.388327] Simple Boot Flag at 0x79 set to 0x1
[    1.389231] audit: initializing netlink socket (disabled)
[    1.389252] type=2000 audit(1240423746.388:1): initialized
[    1.395102] highmem bounce pool size: 64 pages
[    1.395109] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.397326] VFS: Disk quotas dquot_6.5.1
[    1.397416] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.397515] msgmni has been set to 1743
[    1.397636] io scheduler noop registered
[    1.397638] io scheduler anticipatory registered
[    1.397641] io scheduler deadline registered
[    1.397652] io scheduler cfq registered (default)
[    1.397823] pci 0000:01:00.0: Boot video device
[    1.397946] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.397984] pcieport-driver 0000:00:01.0: found MSI capability
[    1.398017] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.398058] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.398096] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.398188] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.398240] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.398290] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.398328] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.398366] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.398480] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.398532] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.398582] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.398622] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.398660] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.398772] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.398824] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.398875] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.398913] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.398950] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.399069] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.399121] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.399171] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.399209] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.399251] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.399596] isapnp: Scanning for PnP cards...
[    1.753716] isapnp: No Plug & Play device found
[    1.784148] hpet_resources: 0xfed00000 is busy
[    1.784254] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.786249] brd: module loaded
[    1.786313] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.786423] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.789615] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.789621] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.789863] mice: PS/2 mouse device common for all mice
[    1.789977] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.790008] rtc0: alarms up to one month, y3k, hpet irqs
[    1.790125] EISA: Probing bus 0 at eisa.0
[    1.790178] EISA: Mainboard O__FFFF detected.
[    1.790218] Cannot allocate resource for EISA slot 1
[    1.790250] EISA: Detected 0 cards.
[    1.790253] cpuidle: using governor ladder
[    1.790255] cpuidle: using governor menu
[    1.790764] TCP cubic registered
[    1.790793] Using IPI No-Shortcut mode
[    1.790954] registered taskstats version 1
[    1.791094]   Magic number: 5:167:191
[    1.791116] tty ttys3: hash matches
[    1.791170] acpi device:1d: hash matches
[    1.791209] rtc_cmos 00:03: setting system clock to 2009-04-22 18:09:07 UTC (1240423747)
[    1.791212] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.791214] EDD information not available.
[    1.791413] Freeing unused kernel memory: 428k freed
[    1.791450] Write protecting the kernel text: 2580k
[    1.791475] Write protecting the kernel read-only data: 940k
[    1.793450] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.964065] fuse init (API version 7.9)
[    2.008458] ACPI: SSDT 7FE6E4F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.008869] ACPI: SSDT 7FE6DE88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.009281] Monitor-Mwait will be used to enter C-1 state
[    2.009284] Monitor-Mwait will be used to enter C-2 state
[    2.009287] Monitor-Mwait will be used to enter C-3 state
[    2.009462] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.009515] processor ACPI0007:00: registered as cooling_device0
[    2.009519] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.009857] ACPI: SSDT 7FE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.010204] ACPI: SSDT 7FE6E46D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.016005] Marking TSC unstable due to TSC halts in idle
[    2.021380] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.021428] processor ACPI0007:01: registered as cooling_device1
[    2.021432] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.027552] thermal LNXTHERM:01: registered as thermal_zone0
[    2.031400] ACPI: Thermal Zone [THM] (48 C)
[    2.438642] usbcore: registered new interface driver usbfs
[    2.438667] usbcore: registered new interface driver hub
[    2.438710] usbcore: registered new device driver usb
[    2.441921] USB Universal Host Controller Interface driver v3.0
[    2.441968] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.441980] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.441987] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.442028] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.442079] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.442222] usb usb1: configuration #1 chosen from 1 choice
[    2.442249] hub 1-0:1.0: USB hub found
[    2.442255] hub 1-0:1.0: 2 ports detected
[    2.471654] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.636943] No dock devices found.
[    2.650855] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.650869] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.650875] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.650900] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.650952] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.651052] usb usb2: configuration #1 chosen from 1 choice
[    2.651079] hub 2-0:1.0: USB hub found
[    2.651086] hub 2-0:1.0: 2 ports detected
[    2.652795] SCSI subsystem initialized
[    2.677997] libata version 3.00 loaded.
[    2.752318] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.752336] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.752340] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.752366] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.756278] ehci_hcd 0000:00:1a.7: debug port 1
[    2.756286] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.756300] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.765036] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.776100] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.776264] usb usb3: configuration #1 chosen from 1 choice
[    2.776292] hub 3-0:1.0: USB hub found
[    2.776301] hub 3-0:1.0: 4 ports detected
[    2.833111] hub 1-0:1.0: unable to enumerate USB device on port 2
[    2.984323] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.984334] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.984338] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.984364] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.984396] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.984489] usb usb4: configuration #1 chosen from 1 choice
[    2.984519] hub 4-0:1.0: USB hub found
[    2.984528] hub 4-0:1.0: 2 ports detected
[    3.192360] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.192372] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.192377] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.192407] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    3.192437] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    3.192534] usb usb5: configuration #1 chosen from 1 choice
[    3.192560] hub 5-0:1.0: USB hub found
[    3.192566] hub 5-0:1.0: 2 ports detected
[    3.296315] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.296322] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.296326] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.296353] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.296381] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.296471] usb usb6: configuration #1 chosen from 1 choice
[    3.296497] hub 6-0:1.0: USB hub found
[    3.296503] hub 6-0:1.0: 2 ports detected
[    3.368084] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    3.500093] Clocksource tsc unstable (delta = -432097679 ns)
[    3.504383] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.504397] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.504401] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.504425] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.508342] ehci_hcd 0000:00:1d.7: debug port 1
[    3.508350] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.508355] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.548083] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.548204] usb usb7: configuration #1 chosen from 1 choice
[    3.548232] hub 7-0:1.0: USB hub found
[    3.548238] hub 7-0:1.0: 6 ports detected
[    3.596428] usb 1-2: configuration #1 chosen from 1 choice
[    3.598442] hub 1-2:1.0: USB hub found
[    3.600175] hub 1-2:1.0: 3 ports detected
[    3.757307] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.757338] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.757352] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.757414] ahci 0000:00:1f.2: version 3.0
[    3.757425] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.757528] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    3.757532] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.757538] ahci 0000:00:1f.2: setting latency timer to 64
[    3.757672] tg3.c:v3.94 (August 14, 2008)
[    3.757695] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.757709] tg3 0000:09:00.0: setting latency timer to 64
[    3.758684] scsi0 : ahci
[    3.759340] scsi1 : ahci
[    3.760031] scsi2 : ahci
[    3.760344] ata1: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 218
[    3.760347] ata2: DUMMY
[    3.760350] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 218
[    4.073484] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:15:c5:81:6b:02
[    4.073488] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    4.073491] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.248150] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.312070] usb 7-1: new high speed USB device using ehci_hcd and address 2
[    4.445763] usb 7-1: configuration #1 chosen from 1 choice
[    4.446072] hub 7-1:1.0: USB hub found
[    4.446175] hub 7-1:1.0: 4 ports detected
[    4.580338] ata1.00: ATA-7: TOSHIBA MK1637GSX, DL040D, max UDMA/100
[    4.580344] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    4.581350] ata1.00: configured for UDMA/100
[    4.764070] usb 7-2: new high speed USB device using ehci_hcd and address 3
[    4.897693] usb 7-2: configuration #1 chosen from 1 choice
[    4.916082] ata3: SATA link down (SStatus 0 SControl 300)
[    4.932218] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL04 PQ: 0 ANSI: 5
[    4.932378] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.990865] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.999288] ata_piix 0000:00:1f.1: version 2.12
[    4.999301] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.999347] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.999453] scsi3 : ata_piix
[    5.000593] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.000808] scsi4 : ata_piix
[    5.001621] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    5.001624] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    5.014186] Driver 'sd' needs updating - please use bus_type methods
[    5.014279] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.014296] sd 0:0:0:0: [sda] Write Protect is off
[    5.014298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.014325] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.014387] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.014402] sd 0:0:0:0: [sda] Write Protect is off
[    5.014404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.014431] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.014434]  sda:<6>usb 7-6: new high speed USB device using ehci_hcd and address 4
[    5.081749]  sda1 sda2 sda3 sda4
[    5.113196] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.164608] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-S10N, A103, max UDMA/33
[    5.180535] ata4.00: configured for UDMA/33
[    5.180579] ata5: port disabled. ignoring.
[    5.183618] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-S10N A103 PQ: 0 ANSI: 5
[    5.183787] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    5.187518] usb 7-6: configuration #1 chosen from 1 choice
[    5.215526] Driver 'sr' needs updating - please use bus_type methods
[    5.220681] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda caddy
[    5.220685] Uniform CD-ROM driver Revision: 3.20
[    5.220774] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.262147] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[    5.386317] usb 1-2.1: configuration #1 chosen from 1 choice
[    5.473174] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[    5.603518] usb 1-2.2: configuration #1 chosen from 1 choice
[    5.681174] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[    5.811301] usb 1-2.3: configuration #1 chosen from 1 choice
[    5.904191] usb 7-1.3: new high speed USB device using ehci_hcd and address 5
[    6.012578] usb 7-1.3: configuration #1 chosen from 1 choice
[    6.012713] hub 7-1.3:1.0: USB hub found
[    6.012798] hub 7-1.3:1.0: 4 ports detected
[    6.264203] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc00030b9a470]
[    6.308197] usb 7-1.4: new low speed USB device using ehci_hcd and address 6
[    6.422572] usb 7-1.4: configuration #1 chosen from 1 choice
[    6.525197] usb 7-1.3.1: new full speed USB device using ehci_hcd and address 7
[    6.639588] usb 7-1.3.1: configuration #1 chosen from 1 choice
[    6.736196] usb 7-1.3.2: new full speed USB device using ehci_hcd and address 8
[    6.851444] usb 7-1.3.2: configuration #1 chosen from 1 choice
[    6.940199] usb 7-1.3.4: new low speed USB device using ehci_hcd and address 9
[    7.053965] usb 7-1.3.4: configuration #1 chosen from 1 choice
[    7.054900] usbcore: registered new interface driver hiddev
[    7.054947] usbcore: registered new interface driver libusual
[    7.058391] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[    7.061900] Initializing USB Mass Storage driver...
[    7.061972] scsi5 : SCSI emulation for USB Mass Storage devices
[    7.062068] usb-storage: device found at 3
[    7.062070] usb-storage: waiting for device to settle before scanning
[    7.072048] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[    7.076492] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input3
[    7.077195] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[    7.080220] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.4/7-1.4:1.0/input/input4
[    7.081177] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-1.4
[    7.086592] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.4/7-1.4:1.1/input/input5
[    7.089205] input,hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-1.4
[    7.091496] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.3/7-1.3.4/7-1.3.4:1.0/input/input6
[    7.093168] input,hidraw4: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-1.3.4
[    7.097949] Fixing up Logitech keyboard report descriptor
[    7.098724] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.3/7-1.3.4/7-1.3.4:1.1/input/input7
[    7.099055] input,hiddev97,hidraw5: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-1.3.4
[    7.099117] usbcore: registered new interface driver usbhid
[    7.099121] usbhid: v2.6:USB HID core driver
[    7.099123] usbcore: registered new interface driver usb-storage
[    7.099127] USB Mass Storage support registered.
[    7.176380] PM: Starting manual resume from disk
[    7.176383] PM: Resume from partition 8:4
[    7.176385] PM: Checking hibernation image.
[    7.176611] PM: Resume from disk failed.
[    7.195717] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.195720] EXT3-fs: write access will be enabled during recovery.
[    7.449092] kjournald starting.  Commit interval 5 seconds
[    7.449106] EXT3-fs: sda3: orphan cleanup on readonly fs
[    7.449112] ext3_orphan_cleanup: deleting unreferenced inode 672578
[    7.449148] ext3_orphan_cleanup: deleting unreferenced inode 458765
[    7.449161] EXT3-fs: sda3: 2 orphan inodes deleted
[    7.449163] EXT3-fs: recovery complete.
[    7.468579] EXT3-fs: mounted filesystem with ordered data mode.
[   12.060348] usb-storage: device scan complete
[   12.060998] scsi 5:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[   12.062068] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   12.062574] sd 5:0:0:0: [sdb] Write Protect is off
[   12.062576] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   12.062579] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   12.063342] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   12.063988] sd 5:0:0:0: [sdb] Write Protect is off
[   12.063992] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   12.063995] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   12.064025]  sdb:<6>udevd version 124 started
[   15.813000]  sdb1
[   15.813128] sd 5:0:0:0: [sdb] Attached SCSI disk
[   15.813259] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   16.107156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.150482] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.202018] Linux agpgart interface v0.103
[   16.243181] ACPI: AC Adapter [AC] (on-line)
[   16.340599] ACPI: Battery Slot [BAT0] (battery present)
[   16.341908] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input8
[   16.342412] ACPI: Lid Switch [LID]
[   16.342472] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input9
[   16.365036] ACPI: Power Button (CM) [PBTN]
[   16.365138] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input10
[   16.397024] ACPI: Sleep Button (CM) [SBTN]
[   16.401155] ACPI: WMI: Mapper loaded
[   16.594704] acpi device:32: registered as cooling_device2
[   16.595850] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input11
[   16.616044] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.833671] udev: renamed network interface eth0 to eth1
[   16.940216] Bluetooth: Core ver 2.13
[   16.940854] NET: Registered protocol family 31
[   16.940857] Bluetooth: HCI device and connection manager initialized
[   16.940860] Bluetooth: HCI socket layer initialized
[   17.080717] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.080721] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   17.081162] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.081177] iwl3945 0000:0c:00.0: setting latency timer to 64
[   17.081197] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.202009] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   17.203529] usbcore: registered new interface driver btusb
[   17.214150] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   17.214573] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.282114] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.282135] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.378762] Registered led device: xpad0
[   17.378851] input: RedOctane Guitar Hero X-plorer as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.3/7-1.3.1/7-1.3.1:1.0/input/input12
[   17.378889] Registered led device: xpad1
[   17.378966] input: RedOctane Guitar Hero X-plorer as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.3/7-1.3.2/7-1.3.2:1.0/input/input13
[   17.378990] usbcore: registered new interface driver xpad
[   17.378993] xpad: X-Box pad driver
[   17.511820] iwl3945 0000:0c:00.0: PCI INT A disabled
[   17.516108] Linux video capture interface: v2.00
[   17.625128] iTCO_vendor_support: vendor-support=0
[   17.640222] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.640312] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   17.640414] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.673159] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   17.673535] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   17.679972] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input14
[   17.690695] sdhci: Secure Digital Host Controller Interface driver
[   17.690698] sdhci: Copyright(c) Pierre Ossman
[   17.692786] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   17.692805] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   17.695877] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   17.708143] input: PC Speaker as /devices/platform/pcspkr/input/input15
[   17.861197] usbcore: registered new interface driver uvcvideo
[   17.861201] USB Video Class driver (v0.1.0)
[   18.532202] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000
[   18.571902] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input16
[   18.627301] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.477429] lp: driver loaded but no devices found
[   27.692123] Adding 3943948k swap on /dev/sda4.  Priority:-1 extents:1 across:3943948k
[   28.234992] EXT3 FS on sda3, internal journal
[   30.343225] kjournald starting.  Commit interval 5 seconds
[   30.343556] EXT3 FS on sda2, internal journal
[   30.343563] EXT3-fs: mounted filesystem with ordered data mode.
[   30.552623] type=1505 audit(1240416576.247:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4777
[   30.600228] type=1505 audit(1240416576.292:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4782
[   30.762647] type=1505 audit(1240416576.456:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4786
[   30.762841] type=1505 audit(1240416576.456:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4786
[   30.882365] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.937106] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   30.937935] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   30.937938] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   30.937941] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   31.092366] NET: Registered protocol family 10
[   31.093019] lo: Disabled Privacy Extensions
[   31.127959] ip6_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by dhughes on 2009-04-22
> **frecon said:**
> A few times the past few weeks Ubuntu have been rebooting or shut down the computer without me doing it. I can't find a common factor for what is causing the sudden reboots and shutdowns. Sometimes it have happen when I've been surfing the net, sometimes when doing something else. Is there a way to check what's actually going on here? Is there a system log that I can check for abnormalities?

Thanks in advance for your reply.


 I had exactly the same problem recently, I thought it was due to the Ubuntu 9.04 Beta I was trying and then I went back to 8.10 it did the same thing, so I tried Kubuntu 8.10 but it did it too. Log files didn't reveal much other than it did reboot as **last -i 20** showed.

 It turned out to be a failing power supply (less than a year old) as soon as I replaced it all is well. Although I couldn't see anything physically wrong with the power supply (capacitors looked fine, no swelling) the new power supply, as I said, fixed the problem. 

[http://ubuntuforums.org/showthread.php?t=1112028](http://ubuntuforums.org/showthread.php?t=1112028)

---

### Post by codeseer on 2009-04-22
Yeah, generally you can look to hardware for random restarts.

Off the top of my head, check:

[LIST=1]
[*]Video card, CPU, etc temperatures
[*]Look at the voltage readings from the power supply
[*]Run a memcheck from the Ubuntu Live CD
[/LIST]

Edit:

Also, if you've been in your case for anything--installing new hardware, blowing dust out, anything--check the cables and slots to make sure everything is in properly.

---

### Post by dhughes on 2009-04-22
> **codeseer said:**
> Yeah, generally you can look to hardware for random restarts.

Off the top of my head, check:

[LIST=1]
[*]Video card, CPU, etc temperatures
[*]Look at the voltage readings from the power supply
[*]Run a memcheck from the Ubuntu Live CD
[/LIST]

Edit:

Also, if you've been in your case for anything--installing new hardware, blowing dust out, anything--check the cables and slots to make sure everything is in properly.

 Yes frecon should definitely do that, check the BIOS for auto shutdown for CPU temp it may be set too low. 

 I did two of the three steps above but bought a power supply anyway because they are fairly cheap (about $40) but mainly because my multimeter died and a power supply was as much as a meter so I just bought the power supply...and got a new multimeter for my birthday a few days later!

---

### Post by frecon on 2009-04-22
Thanks so much for you replies! :) I will check them out asap.

I got a new power supply a few months ago so I don't think it's that. But I will definitely test it.

---

### Post by frecon on 2009-05-22
I think the problem has something to do with
```
Clocksource tsc unstable (delta = -154760436 ns)
```
found in /var/log/messages just before Ubuntu freezes or crashes. polobreaka seem to have the same problem and [solved it by changing cpu setting to performance]("http://ubuntuforums.org/showpost.php?p=6768897&postcount=9"). I've changed to performance now to see if it works. But, it seem to be a rather bad solution. Especially for a laptop that need to think about battery drain. Isn't there another way to solve this?

---

### Post by frecon on 2009-05-23
I've been testing to boot with clocksource=hpet acpi=off noacpi as suggested in this [solution to the tsc clocksource unstable problem]("http://ubuntuforums.org/showpost.php?p=5423053&postcount=13") post but it didn't work. Ubuntu still crashes/freezes. But, this time it doesn't show Clocksource tsc unstable (delta = -154760436 ns) in /var/log/messages. This the output just before the latest two crashes:
```
May 23 21:04:13 frej-laptop pulseaudio[4841]: module-alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May 23 21:04:13 frej-laptop pulseaudio[4841]: module-alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May 23 21:04:54 frej-laptop kernel: [  845.790738] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT

```
```
May 23 23:39:26 frej-laptop kernel: [  380.822961] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 23 23:39:28 frej-laptop kernel: [  382.397921] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 23 23:39:28 frej-laptop kernel: [  382.397923] Bluetooth: BNEP filters: protocol multicast
May 23 23:39:28 frej-laptop kernel: [  382.439928] Bridge firewalling registered
May 23 23:39:30 frej-laptop kernel: [  384.244040] ppdev: user-space parallel port driver
May 23 23:39:32 frej-laptop kernel: [  386.594194] nvidia: module license 'NVIDIA' taints kernel.
May 23 23:39:32 frej-laptop kernel: [  386.875248] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
May 23 23:39:32 frej-laptop kernel: [  386.876130] NVRM: failed to register with the ACPI subsystem!
May 23 23:39:32 frej-laptop kernel: [  386.993881] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread F54925B0 could not acquire Mutex [1] [20080926]
May 23 23:39:34 frej-laptop kernel: [  388.330275] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 23 23:39:34 frej-laptop kernel: [  388.376294] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-1.ucode
May 23 23:39:34 frej-laptop kernel: [  388.848362] Registered led device: iwl-phy0:radio
May 23 23:39:34 frej-laptop kernel: [  388.848377] Registered led device: iwl-phy0:assoc
May 23 23:39:34 frej-laptop kernel: [  388.848425] Registered led device: iwl-phy0:RX
May 23 23:39:34 frej-laptop kernel: [  388.848437] Registered led device: iwl-phy0:TX
May 23 23:39:34 frej-laptop kernel: [  388.860094] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 23 23:59:12 frej-laptop -- MARK --
May 24 00:08:06 frej-laptop pulseaudio[10318]: module-alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May 24 00:08:06 frej-laptop pulseaudio[10318]: module-alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May 24 00:10:02 frej-laptop kernel: [ 2217.088576] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 24 00:10:08 frej-laptop kernel: [ 2222.782035] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT

```
```
frej@frej-laptop:~$ last -i
frej     pts/1        0.0.0.0          Sun May 24 00:10   still logged in   
frej     pts/0        0.0.0.0          Sun May 24 00:09   still logged in   
frej     tty7         0.0.0.0          Sun May 24 00:08   still logged in   
reboot   system boot  0.0.0.0          Sat May 23 23:39 - 00:29  (00:50)    
frej     pts/0        0.0.0.0          Sat May 23 23:29 - crash  (00:09)    
frej     tty7         0.0.0.0          Sat May 23 21:04 - crash  (02:35)    
reboot   system boot  0.0.0.0          Sat May 23 20:51 - 00:29  (03:38)    

```
Any idea on what's causing the crashes and freezes? I'm feeling so frustrated now. ](*,)

---

