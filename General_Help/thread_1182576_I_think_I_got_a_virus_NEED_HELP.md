---
title: "I think I got a virus? NEED HELP"
date: 2009-06-09
forum: General Help
---

### Post by ubucrap on 2009-06-09
I'm on a Dell laptop with 2.0 ghz duo core Intel processor, 320gb hdd.
This is what happened
I was running XP in Virtual Box on Ubuntu Ibex.
Inside XP I was running iTunes and was syncing my iPod. 
I had torrented quite a few programs, which may or may not have been open source, and installed one of those programs on XP in the past 24 hours.
I moved out of the VB "window" to remove a usb thumb drive, and when I ejected it, I emptied the trash.
As soon as I started emptying the trash, things started dissapearing off of my desktop. It happened VERY quickly. In about 5 seconds 1/2 my desktop was gone, then my screen blinked and I lost the background picture.
I was so thoroughly confused, so I tried to close VB, which took a moment, but did respond and closed out.
Then I tried to open System Monitor one 3 different desktops, but it froze on each one. I then quit Transmisison, bit torrent client, and everything was gone but two files from my desktop.
I rebooted and everything is gone, but the programs on my hdd.
Does this make sense for a virus?
What could possibly have happened?
Is there anyway to revert these terrible changes?

---

### Post by coffeecat on 2009-06-09
A few thoughts.

If you've acquired a Windows virus somehow, it will only affect your virtual XP. Windows executable viruses cannot run in Linux, and the destructive behaviour you've seen happened in your Linux environment, not the virtual Windows one. However, have you a shared folder between Ubuntu and the Windows guest? Have you by chance shared the whole of your home folder with the Windows guest? If that were so, a Windows virus running amok could conceivably also run amok in your Linux home folder.

When you say that when you rebooted everything was gone but 'programs on your hdd', what precisely do you mean? Can you log in to your account? Is the VB guest still there? Have any of your personal files been deleted?

---

### Post by 3rdalbum on 2009-06-09
Not a virus. It sounds like there was something in your trash can that should not have been there (and has referenced itself as your home directory?), but I'm darned if I know what it could have been.

Anyone got any ideas? It's not the "user's Home" icon from the desktop, as that doesn't go into the trash; and it's not a symbolic link as those just delete the link and not the link's target.

---

### Post by ubucrap on 2009-06-09
> **coffeecat said:**
> A few thoughts.

If you've acquired a Windows virus somehow, it will only affect your virtual XP. Windows executable viruses cannot run in Linux, and the destructive behaviour you've seen happened in your Linux environment, not the virtual Windows one. However, have you a shared folder between Ubuntu and the Windows guest? Have you by chance shared the whole of your home folder with the Windows guest? If that were so, a Windows virus running amok could conceivably also run amok in your Linux home folder.

When you say that when you rebooted everything was gone but 'programs on your hdd', what precisely do you mean? Can you log in to your account? Is the VB guest still there? Have any of your personal files been deleted?

Yes I can still log in. My user account is still there, and every program I had is still referenced in my applications menu, but all of my files are gone. All of my word documents, all 30gb of music, all videos, all 10gb of pictures, etc. 
I can log into my account & VB is still there, and still will run, but both of the partitions I had are gone (one of WinXP & one of OPENsolaris).

I had shared about 3 directories, which were all located in the Desktop directory, with the WinXP VB partition & had installed VB Guest additions.

So am I just SOL?

---

### Post by finer recliner on 2009-06-09
how did you "empty the trash"?

---

### Post by HereInOz on 2009-06-09
Just remember that if you delete a file or files in Windows, and those files are on a network share, be it a Windows share or a Samba share, those deleted files on the network share do not go to any trash or recycle bin - they are deleted permanently.

Sounds like you may have inadvertently deleted all the files from your home folder from within the Windows system, and they have all been deleted.  If that is indeed the case, then the only way would be to use a hard disk data recovery tool (undelete type of thing) suitable for EXT3.

---

### Post by ubucrap on 2009-06-09
> **finer recliner said:**
> how did you "empty the trash"?

Once I clicked "Unmount Volume" for the jump drive I was using, the message window popped up asking if I wanted to empty the trash. I clicked yes.

As far as now that I am awake and not in panic mode...

There are a couple of updates.
One: I can look in my log files! I'm sorry for not doing this before posting, I was definitely in panic attack mode, as I haven't backed up in the last week because of the extensive amount of work I've been doing on my computer. (I know that is the worst time to stop backing up!)
Two: Windows Vista is possibly the worst thing to happen to technology since Windows ME or aspx
Earlier in the evening, I had plugged that usb jump drive into a machine running Vista to share a file. That file would not copy to Vista and Vista would not eject the volume. 
Three: I had added that jump drive to my VB list of hardware. I think I mentioned earlier, when I plugged in the drive, I was running VB with XP running and my iPod syncing. And I wasn't paying attention to the fact that my virtualized XP machine had probably connected the drive as well, so I unmounted it from Ubuntu OS, but I don't know what it was doing in the XP OS.

The reason I mention this is because my log files are ripe with "Filesystem panic" errors due to "invalid access to FAT"
All of that to say. This is only the second time I've really looked at the logs since my using Ubuntu. 
I love linux, and I like Ubuntu (I've played with a couple other distros and might migrate sometime), but I haven't learned as much as I should in the past couple of years. 
So I'm hoping that someone will be kind enough to help me to know if I can resolve this issue based on the log I'll post below. It is the "syslog" (from about the time of the error).
I appreciate all the help guys!

---

### Post by ubucrap on 2009-06-09
Jun  9 02:29:01 beartop NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Jun  9 02:29:01 beartop NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Jun  9 02:29:01 beartop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Jun  9 02:29:01 beartop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5678 
Jun  9 02:29:01 beartop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Jun  9 02:29:01 beartop avahi-daemon[4777]: Withdrawing address record for 192.168.1.201 on eth0.
Jun  9 02:29:01 beartop avahi-daemon[4777]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Jun  9 02:29:01 beartop avahi-daemon[4777]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  9 02:29:01 beartop NetworkManager: <info>  Policy set 'Auto Bearwork' (eth1) as default for routing and DNS. 
Jun  9 02:29:53 beartop kernel: [  126.292076] CE: hpet increasing min_delta_ns to 15000 nsec
Jun  9 02:29:53 beartop kernel: [  126.292177] CE: hpet increasing min_delta_ns to 22500 nsec
Jun  9 02:29:53 beartop kernel: [  126.292271] CE: hpet increasing min_delta_ns to 33750 nsec
Jun  9 02:32:16 beartop kernel: [  269.324022] CE: hpet increasing min_delta_ns to 50624 nsec
Jun  9 02:33:47 beartop NetworkManager: <debug> [1244532827.644122] periodic_update(): Roamed from BSSID 00:1C:10:C0:88:23 (Bearwork) to (none) ((none)) 
Jun  9 02:33:53 beartop NetworkManager: <debug> [1244532833.646860] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:10:C0:88:23 (Bearwork) 
Jun  9 02:35:33 beartop avahi-daemon[4777]: Invalid legacy unicast query packet.
Jun  9 02:35:33 beartop last message repeated 2 times
Jun  9 02:35:33 beartop avahi-daemon[4777]: Received response with invalid source port 46615 on interface 'eth1.0'
Jun  9 02:36:04 beartop last message repeated 5 times
Jun  9 02:36:36 beartop avahi-daemon[4777]: Received response with invalid source port 46615 on interface 'eth1.0'
Jun  9 02:37:47 beartop NetworkManager: <debug> [1244533067.792821] periodic_update(): Roamed from BSSID 00:1C:10:C0:88:23 (Bearwork) to (none) ((none)) 
Jun  9 02:37:53 beartop NetworkManager: <debug> [1244533073.795791] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:10:C0:88:23 (Bearwork) 
Jun  9 02:39:01 beartop /USR/SBIN/CRON[6916]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun  9 02:39:56 beartop kernel: [  729.745076] usb 1-3: new high speed USB device using ehci_hcd and address 2
Jun  9 02:39:56 beartop kernel: [  729.887425] usb 1-3: configuration #1 chosen from 2 choices
Jun  9 02:39:57 beartop kernel: [  730.021681] usbcore: registered new interface driver libusual
Jun  9 02:39:57 beartop kernel: [  730.064493] Initializing USB Mass Storage driver...
Jun  9 02:39:57 beartop kernel: [  730.066768] scsi2 : SCSI emulation for USB Mass Storage devices
Jun  9 02:39:57 beartop kernel: [  730.067183] usbcore: registered new interface driver usb-storage
Jun  9 02:39:57 beartop kernel: [  730.067399] USB Mass Storage support registered.
Jun  9 02:39:57 beartop kernel: [  730.067702] usb-storage: device found at 2
Jun  9 02:39:57 beartop kernel: [  730.067707] usb-storage: waiting for device to settle before scanning
Jun  9 02:55:38 beartop kernel: [ 1671.248070] usb 1-3: reset high speed USB device using ehci_hcd and address 2
Jun  9 02:55:38 beartop kernel: [ 1671.382090] scsi3 : SCSI emulation for USB Mass Storage devices
Jun  9 02:55:38 beartop kernel: [ 1671.383698] usb-storage: device found at 2
Jun  9 02:55:38 beartop kernel: [ 1671.383713] usb-storage: waiting for device to settle before scanning
Jun  9 02:55:43 beartop kernel: [ 1676.380448] usb-storage: device scan complete
Jun  9 02:55:43 beartop kernel: [ 1676.381384] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Jun  9 02:55:43 beartop kernel: [ 1676.386830] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
Jun  9 02:55:43 beartop kernel: [ 1676.387944] sd 3:0:0:0: [sdb] Write Protect is off
Jun  9 02:55:43 beartop kernel: [ 1676.387960] sd 3:0:0:0: [sdb] Mode Sense: 68 00 00 08
Jun  9 02:55:43 beartop kernel: [ 1676.387968] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 02:55:43 beartop kernel: [ 1676.390205] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
Jun  9 02:55:43 beartop kernel: [ 1676.391835] sd 3:0:0:0: [sdb] Write Protect is off
Jun  9 02:55:43 beartop kernel: [ 1676.391848] sd 3:0:0:0: [sdb] Mode Sense: 68 00 00 08
Jun  9 02:55:43 beartop kernel: [ 1676.391855] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 02:55:45 beartop kernel: [ 1676.392881]  sdb: sdb1 sdb2
Jun  9 02:55:45 beartop kernel: [ 1678.802150] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jun  9 02:55:45 beartop kernel: [ 1678.803593] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jun  9 02:55:48 beartop hald: mounted /dev/sdb2 on behalf of uid 1000
Jun  9 02:59:12 beartop hald: unmounted /dev/sdb2 from '/media/BEARPOD' on behalf of uid 1000
Jun  9 02:59:30 beartop kernel: [ 1903.857055] usb 1-3: reset high speed USB device using ehci_hcd and address 2
Jun  9 02:59:53 beartop avahi-daemon[4777]: Invalid legacy unicast query packet.
Jun  9 02:59:54 beartop last message repeated 2 times
Jun  9 02:59:54 beartop avahi-daemon[4777]: Received response with invalid source port 33228 on interface 'eth1.0'
Jun  9 02:59:55 beartop avahi-daemon[4777]: Received response with invalid source port 33228 on interface 'eth1.0'
Jun  9 02:59:57 beartop kernel: [ 1930.066638] usb 1-3: USB disconnect, address 2
Jun  9 02:59:57 beartop avahi-daemon[4777]: Received response with invalid source port 33228 on interface 'eth1.0'
Jun  9 03:00:25 beartop last message repeated 3 times
Jun  9 03:01:27 beartop kernel: [ 2020.652081] usb 1-7: new high speed USB device using ehci_hcd and address 3
Jun  9 03:01:27 beartop kernel: [ 2020.792720] usb 1-7: configuration #1 chosen from 1 choice
Jun  9 03:01:27 beartop kernel: [ 2020.832082] scsi4 : SCSI emulation for USB Mass Storage devices
Jun  9 03:01:27 beartop kernel: [ 2020.844082] usb-storage: device found at 3
Jun  9 03:01:27 beartop kernel: [ 2020.844095] usb-storage: waiting for device to settle before scanning
Jun  9 03:01:32 beartop kernel: [ 2025.844398] usb-storage: device scan complete
Jun  9 03:01:32 beartop kernel: [ 2025.845309] scsi 4:0:0:0: Direct-Access     Simple   Bonzai Xpress    0.00 PQ: 0 ANSI: 2
Jun  9 03:01:32 beartop kernel: [ 2025.873655] sd 4:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:01:32 beartop kernel: [ 2025.874257] sd 4:0:0:0: [sdb] Write Protect is off
Jun  9 03:01:32 beartop kernel: [ 2025.874271] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:01:32 beartop kernel: [ 2025.874281] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:01:32 beartop kernel: [ 2025.876137] sd 4:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:01:32 beartop kernel: [ 2025.876746] sd 4:0:0:0: [sdb] Write Protect is off
Jun  9 03:01:32 beartop kernel: [ 2025.876759] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:01:32 beartop kernel: [ 2025.876767] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:01:32 beartop kernel: [ 2025.876781]  sdb: sdb1
Jun  9 03:01:32 beartop kernel: [ 2025.981532] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jun  9 03:01:32 beartop kernel: [ 2025.981798] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jun  9 03:01:33 beartop hald: mounted /dev/sdb1 on behalf of uid 1000
Jun  9 03:01:36 beartop kernel: [ 2029.681364] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:36 beartop kernel: [ 2029.681375]     invalid access to FAT (entry 0x38653837)
Jun  9 03:01:36 beartop kernel: [ 2029.681380]     File system has been set read-only
Jun  9 03:01:36 beartop kernel: [ 2029.682261] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:36 beartop kernel: [ 2029.682269]     invalid access to FAT (entry 0x61342d35)
Jun  9 03:01:38 beartop kernel: [ 2031.581357] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:38 beartop kernel: [ 2031.581376]     invalid access to FAT (entry 0x38653837)
Jun  9 03:01:38 beartop kernel: [ 2031.599562] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:38 beartop kernel: [ 2031.599577]     invalid access to FAT (entry 0x61342d35)
Jun  9 03:01:38 beartop kernel: [ 2031.731872] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:38 beartop kernel: [ 2031.731882]     invalid access to FAT (entry 0x84628930)
Jun  9 03:01:38 beartop kernel: [ 2031.762109] FAT: Filesystem panic (dev sdb1)
Jun  9 03:01:38 beartop kernel: [ 2031.762119]     invalid access to FAT (entry 0x7ae8e219)
Jun  9 03:09:01 beartop /USR/SBIN/CRON[8807]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun  9 03:10:08 beartop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Jun  9 03:10:18 beartop kernel: [ 2551.727521] usb 1-7: USB disconnect, address 3
Jun  9 03:10:23 beartop kernel: [ 2556.420118] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jun  9 03:10:23 beartop kernel: [ 2556.558770] usb 1-3: configuration #1 chosen from 1 choice
Jun  9 03:10:23 beartop kernel: [ 2556.559933] scsi5 : SCSI emulation for USB Mass Storage devices
Jun  9 03:10:23 beartop kernel: [ 2556.561184] usb-storage: device found at 4
Jun  9 03:10:23 beartop kernel: [ 2556.561196] usb-storage: waiting for device to settle before scanning
Jun  9 03:10:28 beartop kernel: [ 2561.560378] usb-storage: device scan complete
Jun  9 03:10:28 beartop kernel: [ 2561.561297] scsi 5:0:0:0: Direct-Access     Simple   Bonzai Xpress    0.00 PQ: 0 ANSI: 2
Jun  9 03:10:28 beartop kernel: [ 2561.564015] sd 5:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:10:28 beartop kernel: [ 2561.564497] sd 5:0:0:0: [sdb] Write Protect is off
Jun  9 03:10:28 beartop kernel: [ 2561.564505] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:10:28 beartop kernel: [ 2561.564512] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:10:28 beartop kernel: [ 2561.569751] sd 5:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:10:28 beartop kernel: [ 2561.570624] sd 5:0:0:0: [sdb] Write Protect is off
Jun  9 03:10:28 beartop kernel: [ 2561.570636] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:10:28 beartop kernel: [ 2561.570643] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:10:28 beartop kernel: [ 2561.571365]  sdb: sdb1
Jun  9 03:10:28 beartop kernel: [ 2561.678653] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jun  9 03:10:28 beartop kernel: [ 2561.678888] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jun  9 03:10:29 beartop hald: mounted /dev/sdb1 on behalf of uid 1000
Jun  9 03:12:15 beartop avahi-daemon[4777]: Invalid legacy unicast query packet.
Jun  9 03:12:16 beartop last message repeated 2 times
Jun  9 03:12:16 beartop avahi-daemon[4777]: Received response with invalid source port 45007 on interface 'eth1.0'
Jun  9 03:12:47 beartop last message repeated 5 times
Jun  9 03:13:19 beartop avahi-daemon[4777]: Received response with invalid source port 45007 on interface 'eth1.0'
Jun  9 03:17:02 beartop /USR/SBIN/CRON[9460]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  9 03:17:05 beartop kernel: [ 2958.669088] usb 1-1: new high speed USB device using ehci_hcd and address 5
Jun  9 03:17:05 beartop kernel: [ 2958.804974] usb 1-1: configuration #1 chosen from 2 choices
Jun  9 03:17:05 beartop kernel: [ 2958.807271] scsi6 : SCSI emulation for USB Mass Storage devices
Jun  9 03:17:05 beartop kernel: [ 2958.808492] usb-storage: device found at 5
Jun  9 03:17:05 beartop kernel: [ 2958.808503] usb-storage: waiting for device to settle before scanning
Jun  9 03:22:47 beartop kernel: [ 3300.342948] FAT: Filesystem panic (dev sdb1)
Jun  9 03:22:47 beartop kernel: [ 3300.342968]     invalid access to FAT (entry 0x6d722022)
Jun  9 03:22:47 beartop kernel: [ 3300.342978]     File system has been set read-only
Jun  9 03:22:47 beartop kernel: [ 3300.344006] FAT: Filesystem panic (dev sdb1)
Jun  9 03:22:47 beartop kernel: [ 3300.344021]     invalid access to FAT (entry 0x30307474)

100-200 more errors like that...

Jun  9 03:24:41 beartop kernel: [ 3414.155284] usb 1-1: USB disconnect, address 5
Jun  9 03:26:56 beartop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Jun  9 03:28:10 beartop syslogd 1.5.0#2ubuntu6: restart.
Jun  9 03:28:10 beartop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Jun  9 03:28:10 beartop kernel: Cannot find map file.
Jun  9 03:28:10 beartop kernel: Loaded 51659 symbols from 92 modules.
Jun  9 03:28:10 beartop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  9 03:28:10 beartop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  9 03:28:10 beartop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
Jun  9 03:28:10 beartop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jun  9 03:28:10 beartop kernel: [    0.000000] DMI 2.4 present.
Jun  9 03:28:10 beartop kernel: [    0.000000] last_pfn = 0x7f6d3 max_arch_pfn = 0x100000
Jun  9 03:28:10 beartop kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Jun  9 03:28:10 beartop kernel: [    0.000000] RAMDISK: 3781b000 - 37fef868
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D70402 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D70402 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D70402 ASL        47)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D70402 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0176 (r1 DELL    M07     27D70402 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D70402 ASL        61)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    0.000000] 1142MB HIGHMEM available.
Jun  9 03:28:10 beartop kernel: [    0.000000] 896MB LOWMEM available.
Jun  9 03:28:10 beartop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Jun  9 03:28:10 beartop kernel: [    0.000000]   low ram: 00000000 - 38000000
Jun  9 03:28:10 beartop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Jun  9 03:28:10 beartop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #4 [003781b000 - 0037fef868]          RAMDISK ==> [003781b000 - 0037fef868]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jun  9 03:28:10 beartop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jun  9 03:28:10 beartop kernel: [    0.000000] Zone PFN ranges:
Jun  9 03:28:10 beartop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun  9 03:28:10 beartop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Jun  9 03:28:10 beartop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f6d3
Jun  9 03:28:10 beartop kernel: [    0.000000] Movable zone start PFN for each node
Jun  9 03:28:10 beartop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun  9 03:28:10 beartop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Jun  9 03:28:10 beartop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f6d3
Jun  9 03:28:10 beartop kernel: [    0.000000] On node 0 totalpages: 521842
Jun  9 03:28:10 beartop kernel: [    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
Jun  9 03:28:10 beartop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jun  9 03:28:10 beartop kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Jun  9 03:28:10 beartop kernel: [    0.000000]   HighMem zone: 289991 pages, LIFO batch:31
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun  9 03:28:10 beartop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  9 03:28:10 beartop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun  9 03:28:10 beartop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun  9 03:28:10 beartop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  9 03:28:10 beartop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun  9 03:28:10 beartop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jun  9 03:28:10 beartop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jun  9 03:28:10 beartop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  9 03:28:10 beartop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jun  9 03:28:10 beartop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Jun  9 03:28:10 beartop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jun  9 03:28:10 beartop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Jun  9 03:28:10 beartop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517254
Jun  9 03:28:10 beartop kernel: [    0.000000] Kernel command line: root=UUID=f3791d18-b232-4476-9e9f-5c93717596b8 ro quiet splash 
Jun  9 03:28:10 beartop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun  9 03:28:10 beartop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun  9 03:28:10 beartop kernel: [    0.000000] Initializing CPU#0
Jun  9 03:28:10 beartop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun  9 03:28:10 beartop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jun  9 03:28:10 beartop kernel: [    0.000000] TSC: using PMTIMER calibration value
Jun  9 03:28:10 beartop kernel: [    0.000000] Detected 1728.992 MHz processor.
Jun  9 03:28:10 beartop kernel: [    0.004000] Console: colour VGA+ 80x25
Jun  9 03:28:10 beartop kernel: [    0.004000] console [tty0] enabled
Jun  9 03:28:10 beartop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun  9 03:28:10 beartop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun  9 03:28:10 beartop kernel: [    0.004000] Memory: 2054240k/2087756k available (2576k kernel code, 32216k reserved, 1164k data, 424k init, 1170252k highmem)
Jun  9 03:28:10 beartop kernel: [    0.004000] virtual kernel memory layout:
Jun  9 03:28:10 beartop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jun  9 03:28:10 beartop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jun  9 03:28:10 beartop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jun  9 03:28:10 beartop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun  9 03:28:10 beartop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Jun  9 03:28:10 beartop kernel: [    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
Jun  9 03:28:10 beartop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03843ea   (2576 kB)
Jun  9 03:28:10 beartop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun  9 03:28:10 beartop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jun  9 03:28:10 beartop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun  9 03:28:10 beartop kernel: [    0.004000] hpet clockevent registered
Jun  9 03:28:10 beartop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.98 BogoMIPS (lpj=6915968)
Jun  9 03:28:10 beartop kernel: [    0.004000] Security Framework initialized
Jun  9 03:28:10 beartop kernel: [    0.004000] SELinux:  Disabled at boot.
Jun  9 03:28:10 beartop kernel: [    0.004000] AppArmor: AppArmor initialized
Jun  9 03:28:10 beartop kernel: [    0.004000] Mount-cache hash table entries: 512
Jun  9 03:28:10 beartop kernel: [    0.004000] Initializing cgroup subsys ns
Jun  9 03:28:10 beartop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jun  9 03:28:10 beartop kernel: [    0.004000] Initializing cgroup subsys memory
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: L2 cache: 1024K
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: Physical Processor ID: 0
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: Processor Core ID: 0
Jun  9 03:28:10 beartop kernel: [    0.004000] using mwait in idle threads.
Jun  9 03:28:10 beartop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jun  9 03:28:10 beartop kernel: [    0.018610] ACPI: Core revision 20080609
Jun  9 03:28:10 beartop kernel: [    0.020589] ACPI: Checking initramfs for custom DSDT
Jun  9 03:28:10 beartop kernel: [    0.419154] ENABLING IO-APIC IRQs
Jun  9 03:28:10 beartop kernel: [    0.419359] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  9 03:28:10 beartop kernel: [    0.459061] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Jun  9 03:28:10 beartop kernel: [    0.460028] Booting processor 1/1 ip 6000
Jun  9 03:28:10 beartop kernel: [    0.004000] Initializing CPU#1
Jun  9 03:28:10 beartop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3457.99 BogoMIPS (lpj=6915998)
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: L2 cache: 1024K
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: Physical Processor ID: 0
Jun  9 03:28:10 beartop kernel: [    0.004000] CPU: Processor Core ID: 1
Jun  9 03:28:10 beartop kernel: [    0.544466] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Jun  9 03:28:10 beartop kernel: [    0.544490] checking TSC synchronization [CPU#0 -> CPU#1]:
Jun  9 03:28:10 beartop kernel: [    0.548031] Measured 3677674845 cycles TSC warp between CPUs, turning off TSC clock.
Jun  9 03:28:10 beartop kernel: [    0.548031] Marking TSC unstable due to check_tsc_sync_source failed
Jun  9 03:28:10 beartop kernel: [    0.548057] Brought up 2 CPUs
Jun  9 03:28:10 beartop kernel: [    0.548061] Total of 2 processors activated (6915.98 BogoMIPS).
Jun  9 03:28:10 beartop kernel: [    0.548087] CPU0 attaching sched-domain:
Jun  9 03:28:10 beartop kernel: [    0.548091]  domain 0: span 0-1 level MC
Jun  9 03:28:10 beartop kernel: [    0.548094]   groups: 0 1
Jun  9 03:28:10 beartop kernel: [    0.548101] CPU1 attaching sched-domain:
Jun  9 03:28:10 beartop kernel: [    0.548104]  domain 0: span 0-1 level MC
Jun  9 03:28:10 beartop kernel: [    0.548107]   groups: 1 0
Jun  9 03:28:10 beartop kernel: [    0.548209] net_namespace: 840 bytes
Jun  9 03:28:10 beartop kernel: [    0.548209] Booting paravirtualized kernel on bare hardware
Jun  9 03:28:10 beartop kernel: [    0.548355] Time:  8:27:45  Date: 06/09/09
Jun  9 03:28:10 beartop kernel: [    0.548390] NET: Registered protocol family 16
Jun  9 03:28:10 beartop kernel: [    0.548416] EISA bus registered
Jun  9 03:28:10 beartop kernel: [    0.548416] ACPI: bus type pci registered
Jun  9 03:28:10 beartop kernel: [    0.548416] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Jun  9 03:28:10 beartop kernel: [    0.548416] PCI: MCFG area at f0000000 reserved in E820
Jun  9 03:28:10 beartop kernel: [    0.548416] PCI: Using MMCONFIG for extended config space
Jun  9 03:28:10 beartop kernel: [    0.548416] PCI: Using configuration type 1 for base access
Jun  9 03:28:10 beartop kernel: [    0.552275] ACPI: EC: Look up EC in DSDT
Jun  9 03:28:10 beartop kernel: [    0.570929] ACPI: Interpreter enabled
Jun  9 03:28:10 beartop kernel: [    0.570934] ACPI: (supports S0 S3 S4 S5)
Jun  9 03:28:10 beartop kernel: [    0.570952] ACPI: Using IOAPIC for interrupt routing
Jun  9 03:28:10 beartop kernel: [    0.604774] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  9 03:28:10 beartop kernel: [    0.604774] PCI: 0000:00:02.0 reg 10 32bit mmio: [eff00000, eff7ffff]
Jun  9 03:28:10 beartop kernel: [    0.604774] PCI: 0000:00:02.0 reg 14 io port: [eff8, efff]
Jun  9 03:28:10 beartop kernel: [    0.604774] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
Jun  9 03:28:10 beartop kernel: [    0.604774] PCI: 0000:00:02.0 reg 1c 32bit mmio: [efec0000, efefffff]
Jun  9 03:28:10 beartop kernel: [    0.604774] PCI: 0000:00:02.1 reg 10 32bit mmio: [eff80000, efffffff]
Jun  9 03:28:10 beartop kernel: [    0.608050] PCI: 0000:00:1b.0 reg 10 64bit mmio: [efebc000, efebffff]
Jun  9 03:28:10 beartop kernel: [    0.608107] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.608114] pci 0000:00:1b.0: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.608188] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.608194] pci 0000:00:1c.0: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.608271] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.608277] pci 0000:00:1c.3: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.608330] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
Jun  9 03:28:10 beartop kernel: [    0.608397] PCI: 0000:00:1d.1 reg 20 io port: [bf60, bf7f]
Jun  9 03:28:10 beartop kernel: [    0.608463] PCI: 0000:00:1d.2 reg 20 io port: [bf40, bf5f]
Jun  9 03:28:10 beartop kernel: [    0.608529] PCI: 0000:00:1d.3 reg 20 io port: [bf20, bf3f]
Jun  9 03:28:10 beartop kernel: [    0.608599] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80000, ffa803ff]
Jun  9 03:28:10 beartop kernel: [    0.608660] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.608666] pci 0000:00:1d.7: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.608832] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jun  9 03:28:10 beartop kernel: [    0.608838] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
Jun  9 03:28:10 beartop kernel: [    0.608887] PCI: 0000:00:1f.2 reg 10 io port: [1f0, 1f7]
Jun  9 03:28:10 beartop kernel: [    0.608896] PCI: 0000:00:1f.2 reg 14 io port: [3f4, 3f7]
Jun  9 03:28:10 beartop kernel: [    0.608905] PCI: 0000:00:1f.2 reg 18 io port: [170, 177]
Jun  9 03:28:10 beartop kernel: [    0.608914] PCI: 0000:00:1f.2 reg 1c io port: [374, 377]
Jun  9 03:28:10 beartop kernel: [    0.608923] PCI: 0000:00:1f.2 reg 20 io port: [bfa0, bfaf]
Jun  9 03:28:10 beartop kernel: [    0.608956] pci 0000:00:1f.2: PME# supported from D3hot
Jun  9 03:28:10 beartop kernel: [    0.608961] pci 0000:00:1f.2: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.609021] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
Jun  9 03:28:10 beartop kernel: [    0.609214] PCI: 0000:0b:00.0 reg 10 32bit mmio: [efdfc000, efdfffff]
Jun  9 03:28:10 beartop kernel: [    0.609462] pci 0000:0b:00.0: supports D1
Jun  9 03:28:10 beartop kernel: [    0.609464] pci 0000:0b:00.0: supports D2
Jun  9 03:28:10 beartop kernel: [    0.609521] PCI: bridge 0000:00:1c.0 32bit mmio: [efd00000, efdfffff]
Jun  9 03:28:10 beartop kernel: [    0.609591] PCI: bridge 0000:00:1c.3 io port: [d000, dfff]
Jun  9 03:28:10 beartop kernel: [    0.609597] PCI: bridge 0000:00:1c.3 32bit mmio: [efa00000, efcfffff]
Jun  9 03:28:10 beartop kernel: [    0.609607] PCI: bridge 0000:00:1c.3 64bit mmio pref: [e0000000, e01fffff]
Jun  9 03:28:10 beartop kernel: [    0.609651] PCI: 0000:03:00.0 reg 10 32bit mmio: [ef9fe000, ef9fffff]
Jun  9 03:28:10 beartop kernel: [    0.609707] pci 0000:03:00.0: supports D1
Jun  9 03:28:10 beartop kernel: [    0.609710] pci 0000:03:00.0: supports D2
Jun  9 03:28:10 beartop kernel: [    0.609712] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.609718] pci 0000:03:00.0: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.609757] PCI: 0000:03:01.0 reg 10 32bit mmio: [ef9fd800, ef9fdfff]
Jun  9 03:28:10 beartop kernel: [    0.609816] pci 0000:03:01.0: supports D1
Jun  9 03:28:10 beartop kernel: [    0.609818] pci 0000:03:01.0: supports D2
Jun  9 03:28:10 beartop kernel: [    0.609821] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.609827] pci 0000:03:01.0: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.609866] PCI: 0000:03:01.1 reg 10 32bit mmio: [ef9fd400, ef9fd4ff]
Jun  9 03:28:10 beartop kernel: [    0.609925] pci 0000:03:01.1: supports D1
Jun  9 03:28:10 beartop kernel: [    0.609927] pci 0000:03:01.1: supports D2
Jun  9 03:28:10 beartop kernel: [    0.609929] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.609935] pci 0000:03:01.1: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.609974] PCI: 0000:03:01.2 reg 10 32bit mmio: [ef9fd500, ef9fd5ff]
Jun  9 03:28:10 beartop kernel: [    0.610033] pci 0000:03:01.2: supports D1
Jun  9 03:28:10 beartop kernel: [    0.610036] pci 0000:03:01.2: supports D2
Jun  9 03:28:10 beartop kernel: [    0.610038] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.610044] pci 0000:03:01.2: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.610083] PCI: 0000:03:01.3 reg 10 32bit mmio: [ef9fd600, ef9fd6ff]
Jun  9 03:28:10 beartop kernel: [    0.610143] pci 0000:03:01.3: supports D1
Jun  9 03:28:10 beartop kernel: [    0.610146] pci 0000:03:01.3: supports D2
Jun  9 03:28:10 beartop kernel: [    0.610148] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.610154] pci 0000:03:01.3: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.610193] PCI: 0000:03:01.4 reg 10 32bit mmio: [ef9fd700, ef9fd7ff]
Jun  9 03:28:10 beartop kernel: [    0.610251] pci 0000:03:01.4: supports D1
Jun  9 03:28:10 beartop kernel: [    0.610253] pci 0000:03:01.4: supports D2
Jun  9 03:28:10 beartop kernel: [    0.610256] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
Jun  9 03:28:10 beartop kernel: [    0.610262] pci 0000:03:01.4: PME# disabled
Jun  9 03:28:10 beartop kernel: [    0.610326] pci 0000:00:1e.0: transparent bridge
Jun  9 03:28:10 beartop kernel: [    0.610335] PCI: bridge 0000:00:1e.0 32bit mmio: [ef900000, ef9fffff]
Jun  9 03:28:10 beartop kernel: [    0.610365] bus 00 -> node 0
Jun  9 03:28:10 beartop kernel: [    0.610373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  9 03:28:10 beartop kernel: [    0.610989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jun  9 03:28:10 beartop kernel: [    0.611173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jun  9 03:28:10 beartop kernel: [    0.611348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jun  9 03:28:10 beartop kernel: [    0.620759] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Jun  9 03:28:10 beartop kernel: [    0.620759] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Jun  9 03:28:10 beartop kernel: [    0.620759] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Jun  9 03:28:10 beartop kernel: [    0.624140] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Jun  9 03:28:10 beartop kernel: [    0.624307] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun  9 03:28:10 beartop kernel: [    0.624478] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun  9 03:28:10 beartop kernel: [    0.624647] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Jun  9 03:28:10 beartop kernel: [    0.624816] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jun  9 03:28:10 beartop kernel: [    0.624920] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun  9 03:28:10 beartop kernel: [    0.624920] pnp: PnP ACPI init
Jun  9 03:28:10 beartop kernel: [    0.624920] ACPI: bus type pnp registered
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.667635] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jun  9 03:28:10 beartop kernel: [    0.668720] pnp: PnP ACPI: found 12 devices
Jun  9 03:28:10 beartop kernel: [    0.668723] ACPI: ACPI bus type pnp unregistered
Jun  9 03:28:10 beartop kernel: [    0.668727] PnPBIOS: Disabled by ACPI PNP
Jun  9 03:28:10 beartop kernel: [    0.668750] PCI: Using ACPI for IRQ routing
Jun  9 03:28:10 beartop kernel: [    0.676043] NET: Registered protocol family 8
Jun  9 03:28:10 beartop kernel: [    0.676046] NET: Registered protocol family 20
Jun  9 03:28:10 beartop kernel: [    0.676067] NetLabel: Initializing
Jun  9 03:28:10 beartop kernel: [    0.676067] NetLabel:  domain hash size = 128
Jun  9 03:28:10 beartop kernel: [    0.676067] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  9 03:28:10 beartop kernel: [    0.676079] NetLabel:  unlabeled traffic allowed by default
Jun  9 03:28:10 beartop kernel: [    0.676089] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun  9 03:28:10 beartop kernel: [    0.676095] hpet0: 3 64-bit timers, 14318180 Hz
Jun  9 03:28:10 beartop kernel: [    0.677737] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jun  9 03:28:10 beartop kernel: [    0.677740]    actual entries 65620
Jun  9 03:28:10 beartop kernel: [    0.677857] AppArmor: AppArmor Filesystem Enabled
Jun  9 03:28:10 beartop kernel: [    0.677888] ACPI: RTC can wake from S4
Jun  9 03:28:10 beartop kernel: [    0.680049] Switched to high resolution mode on CPU 0
Jun  9 03:28:10 beartop kernel: [    0.680526] Switched to high resolution mode on CPU 1
Jun  9 03:28:10 beartop kernel: [    0.684038] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684042] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684046] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684050] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684054] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684058] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684062] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684066] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684071] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684074] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684078] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684082] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684086] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684090] system 00:00: iomem range 0xf4000000-0xf4003fff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684094] system 00:00: iomem range 0xf4004000-0xf4004fff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684098] system 00:00: iomem range 0xf4005000-0xf4005fff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684102] system 00:00: iomem range 0xf4006000-0xf4006fff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684106] system 00:00: iomem range 0xf4008000-0xf400bfff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684110] system 00:00: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684119] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684127] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684131] system 00:03: ioport range 0x1080-0x10bf has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684135] system 00:03: ioport range 0x10c0-0x10df has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684139] system 00:03: ioport range 0x809-0x809 has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684150] system 00:08: ioport range 0xc80-0xcff could not be reserved
Jun  9 03:28:10 beartop kernel: [    0.684154] system 00:08: ioport range 0x910-0x91f has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684157] system 00:08: ioport range 0x920-0x92f has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684161] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684164] system 00:08: ioport range 0x930-0x97f has been reserved
Jun  9 03:28:10 beartop kernel: [    0.684174] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Jun  9 03:28:10 beartop kernel: [    0.719651] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Jun  9 03:28:10 beartop kernel: [    0.719654] pci 0000:00:1c.0:   IO window: disabled
Jun  9 03:28:10 beartop kernel: [    0.719662] pci 0000:00:1c.0:   MEM window: 0xefd00000-0xefdfffff
Jun  9 03:28:10 beartop kernel: [    0.719668] pci 0000:00:1c.0:   PREFETCH window: disabled
Jun  9 03:28:10 beartop kernel: [    0.719677] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
Jun  9 03:28:10 beartop kernel: [    0.719682] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
Jun  9 03:28:10 beartop kernel: [    0.719689] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefcfffff
Jun  9 03:28:10 beartop kernel: [    0.719696] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
Jun  9 03:28:10 beartop kernel: [    0.719705] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Jun  9 03:28:10 beartop kernel: [    0.719708] pci 0000:00:1e.0:   IO window: disabled
Jun  9 03:28:10 beartop kernel: [    0.719715] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
Jun  9 03:28:10 beartop kernel: [    0.719721] pci 0000:00:1e.0:   PREFETCH window: disabled
Jun  9 03:28:10 beartop kernel: [    0.719744] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 03:28:10 beartop kernel: [    0.719750] pci 0000:00:1c.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    0.719762] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun  9 03:28:10 beartop kernel: [    0.719768] pci 0000:00:1c.3: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    0.719777] pci 0000:00:1e.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    0.719782] bus: 00 index 0 io port: [0, ffff]
Jun  9 03:28:10 beartop kernel: [    0.719785] bus: 00 index 1 mmio: [0, ffffffff]
Jun  9 03:28:10 beartop kernel: [    0.719788] bus: 0b index 0 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719790] bus: 0b index 1 mmio: [efd00000, efdfffff]
Jun  9 03:28:10 beartop kernel: [    0.719793] bus: 0b index 2 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719795] bus: 0b index 3 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719798] bus: 0c index 0 io port: [d000, dfff]
Jun  9 03:28:10 beartop kernel: [    0.719801] bus: 0c index 1 mmio: [efa00000, efcfffff]
Jun  9 03:28:10 beartop kernel: [    0.719804] bus: 0c index 2 mmio: [e0000000, e01fffff]
Jun  9 03:28:10 beartop kernel: [    0.719806] bus: 0c index 3 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719809] bus: 03 index 0 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719811] bus: 03 index 1 mmio: [ef900000, ef9fffff]
Jun  9 03:28:10 beartop kernel: [    0.719814] bus: 03 index 2 mmio: [0, 0]
Jun  9 03:28:10 beartop kernel: [    0.719816] bus: 03 index 3 io port: [0, ffff]
Jun  9 03:28:10 beartop kernel: [    0.719819] bus: 03 index 4 mmio: [0, ffffffff]
Jun  9 03:28:10 beartop kernel: [    0.719831] NET: Registered protocol family 2
Jun  9 03:28:10 beartop kernel: [    0.732073] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun  9 03:28:10 beartop kernel: [    0.732377] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun  9 03:28:10 beartop kernel: [    0.733004] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun  9 03:28:10 beartop kernel: [    0.733367] TCP: Hash tables configured (established 131072 bind 65536)
Jun  9 03:28:10 beartop kernel: [    0.733372] TCP reno registered
Jun  9 03:28:10 beartop kernel: [    0.740125] NET: Registered protocol family 1
Jun  9 03:28:10 beartop kernel: [    0.740269] checking if image is initramfs... it is
Jun  9 03:28:10 beartop kernel: [    1.501017] Clocksource tsc unstable (delta = 2127065827 ns)
Jun  9 03:28:10 beartop kernel: [    1.556081] Freeing initrd memory: 8018k freed
Jun  9 03:28:10 beartop kernel: [    1.556305] Simple Boot Flag at 0x79 set to 0x1
Jun  9 03:28:10 beartop kernel: [    1.557700] audit: initializing netlink socket (disabled)
Jun  9 03:28:10 beartop kernel: [    1.557726] type=2000 audit(1244536065.556:1): initialized
Jun  9 03:28:10 beartop kernel: [    1.563820] highmem bounce pool size: 64 pages
Jun  9 03:28:10 beartop kernel: [    1.563830] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun  9 03:28:10 beartop kernel: [    1.566757] VFS: Disk quotas dquot_6.5.1
Jun  9 03:28:10 beartop kernel: [    1.566873] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun  9 03:28:10 beartop kernel: [    1.567005] msgmni has been set to 1743
Jun  9 03:28:10 beartop kernel: [    1.567158] io scheduler noop registered
Jun  9 03:28:10 beartop kernel: [    1.567162] io scheduler anticipatory registered
Jun  9 03:28:10 beartop kernel: [    1.567165] io scheduler deadline registered
Jun  9 03:28:10 beartop kernel: [    1.567180] io scheduler cfq registered (default)
Jun  9 03:28:10 beartop kernel: [    1.567198] pci 0000:00:02.0: Boot video device
Jun  9 03:28:10 beartop kernel: [    1.567456] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    1.567509] pcieport-driver 0000:00:1c.0: found MSI capability
Jun  9 03:28:10 beartop kernel: [    1.567563] pci_express 0000:00:1c.0:pcie00: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.567623] pci_express 0000:00:1c.0:pcie02: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.567673] pci_express 0000:00:1c.0:pcie03: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.567800] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    1.567851] pcieport-driver 0000:00:1c.3: found MSI capability
Jun  9 03:28:10 beartop kernel: [    1.567901] pci_express 0000:00:1c.3:pcie00: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.567950] pci_express 0000:00:1c.3:pcie02: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.567998] pci_express 0000:00:1c.3:pcie03: allocate port service
Jun  9 03:28:10 beartop kernel: [    1.568549] isapnp: Scanning for PnP cards...
Jun  9 03:28:10 beartop kernel: [    1.922489] isapnp: No Plug & Play device found
Jun  9 03:28:10 beartop kernel: [    1.970595] hpet_resources: 0xfed00000 is busy
Jun  9 03:28:10 beartop kernel: [    1.970734] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jun  9 03:28:10 beartop kernel: [    1.973566] brd: module loaded
Jun  9 03:28:10 beartop kernel: [    1.973656] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun  9 03:28:10 beartop kernel: [    1.973804] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun  9 03:28:10 beartop kernel: [    1.976657] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  9 03:28:10 beartop kernel: [    1.976664] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  9 03:28:10 beartop kernel: [    1.977148] mice: PS/2 mouse device common for all mice
Jun  9 03:28:10 beartop kernel: [    1.977327] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jun  9 03:28:10 beartop kernel: [    1.977361] rtc0: alarms up to one month, y3k, hpet irqs
Jun  9 03:28:10 beartop kernel: [    1.977547] EISA: Probing bus 0 at eisa.0
Jun  9 03:28:10 beartop kernel: [    1.977613] EISA: Mainboard N__FFFF detected.
Jun  9 03:28:10 beartop kernel: [    1.977681] Cannot allocate resource for EISA slot 1
Jun  9 03:28:10 beartop kernel: [    1.977715] EISA: Detected 0 cards.
Jun  9 03:28:10 beartop kernel: [    1.977719] cpuidle: using governor ladder
Jun  9 03:28:10 beartop kernel: [    1.977722] cpuidle: using governor menu
Jun  9 03:28:10 beartop kernel: [    1.978354] TCP cubic registered
Jun  9 03:28:10 beartop kernel: [    1.978390] Using IPI No-Shortcut mode
Jun  9 03:28:10 beartop kernel: [    1.978664] registered taskstats version 1
Jun  9 03:28:10 beartop kernel: [    1.978818]   Magic number: 13:447:472
Jun  9 03:28:10 beartop kernel: [    1.978945] acpi LNXSYSTM:00: hash matches
Jun  9 03:28:10 beartop kernel: [    1.978992] rtc_cmos 00:06: setting system clock to 2009-06-09 08:27:47 UTC (1244536067)
Jun  9 03:28:10 beartop kernel: [    1.978996] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  9 03:28:10 beartop kernel: [    1.978998] EDD information not available.
Jun  9 03:28:10 beartop kernel: [    1.979250] Freeing unused kernel memory: 424k freed
Jun  9 03:28:10 beartop kernel: [    1.979308] Write protecting the kernel text: 2580k
Jun  9 03:28:10 beartop kernel: [    1.979347] Write protecting the kernel read-only data: 940k
Jun  9 03:28:10 beartop kernel: [    1.980733] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun  9 03:28:10 beartop kernel: [    2.197208] fuse init (API version 7.9)
Jun  9 03:28:10 beartop kernel: [    2.261614] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    2.262018] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    2.380214] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun  9 03:28:10 beartop kernel: [    2.380294] processor ACPI0007:00: registered as cooling_device0
Jun  9 03:28:10 beartop kernel: [    2.380300] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun  9 03:28:10 beartop kernel: [    2.380729] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    2.381105] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Jun  9 03:28:10 beartop kernel: [    2.381807] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Jun  9 03:28:10 beartop kernel: [    2.381864] processor ACPI0007:01: registered as cooling_device1
Jun  9 03:28:10 beartop kernel: [    2.381870] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun  9 03:28:10 beartop kernel: [    2.388287] thermal LNXTHERM:01: registered as thermal_zone0
Jun  9 03:28:10 beartop kernel: [    2.391914] ACPI: Thermal Zone [THM] (42 C)
Jun  9 03:28:10 beartop kernel: [    2.768633] usbcore: registered new interface driver usbfs
Jun  9 03:28:10 beartop kernel: [    2.768663] usbcore: registered new interface driver hub
Jun  9 03:28:10 beartop kernel: [    2.769052] usbcore: registered new device driver usb
Jun  9 03:28:10 beartop kernel: [    2.792562] USB Universal Host Controller Interface driver v3.0
Jun  9 03:28:10 beartop kernel: [    2.792624] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun  9 03:28:10 beartop kernel: [    2.792636] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    2.792641] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun  9 03:28:10 beartop kernel: [    2.792696] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun  9 03:28:10 beartop kernel: [    2.792737] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
Jun  9 03:28:10 beartop kernel: [    2.792930] usb usb1: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    2.792965] hub 1-0:1.0: USB hub found
Jun  9 03:28:10 beartop kernel: [    2.792974] hub 1-0:1.0: 2 ports detected
Jun  9 03:28:10 beartop kernel: [    2.837333] No dock devices found.
Jun  9 03:28:10 beartop kernel: [    2.856840] SCSI subsystem initialized
Jun  9 03:28:10 beartop kernel: [    2.879212] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Jun  9 03:28:10 beartop kernel: [    2.893351] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun  9 03:28:10 beartop kernel: [    2.893365] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    2.893370] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun  9 03:28:10 beartop kernel: [    2.893409] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun  9 03:28:10 beartop kernel: [    2.893451] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
Jun  9 03:28:10 beartop kernel: [    2.893576] usb usb2: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    2.893610] hub 2-0:1.0: USB hub found
Jun  9 03:28:10 beartop kernel: [    2.893619] hub 2-0:1.0: 2 ports detected
Jun  9 03:28:10 beartop kernel: [    2.937676] libata version 3.00 loaded.
Jun  9 03:28:10 beartop kernel: [    3.104498] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jun  9 03:28:10 beartop kernel: [    3.104512] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    3.104518] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun  9 03:28:10 beartop kernel: [    3.104554] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jun  9 03:28:10 beartop kernel: [    3.104599] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
Jun  9 03:28:10 beartop kernel: [    3.104735] usb usb3: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    3.104775] hub 3-0:1.0: USB hub found
Jun  9 03:28:10 beartop kernel: [    3.104784] hub 3-0:1.0: 2 ports detected
Jun  9 03:28:10 beartop kernel: [    3.208496] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jun  9 03:28:10 beartop kernel: [    3.208511] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    3.208516] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun  9 03:28:10 beartop kernel: [    3.208552] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jun  9 03:28:10 beartop kernel: [    3.208599] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
Jun  9 03:28:10 beartop kernel: [    3.208761] usb usb4: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    3.208796] hub 4-0:1.0: USB hub found
Jun  9 03:28:10 beartop kernel: [    3.208806] hub 4-0:1.0: 2 ports detected
Jun  9 03:28:10 beartop kernel: [    3.216131] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun  9 03:28:10 beartop kernel: [    3.308647] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun  9 03:28:10 beartop kernel: [    3.308664] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    3.308669] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun  9 03:28:10 beartop kernel: [    3.308706] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jun  9 03:28:10 beartop kernel: [    3.312621] ehci_hcd 0000:00:1d.7: debug port 1
Jun  9 03:28:10 beartop kernel: [    3.312629] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun  9 03:28:10 beartop kernel: [    3.312639] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
Jun  9 03:28:10 beartop kernel: [    3.340030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun  9 03:28:10 beartop kernel: [    3.340253] usb usb5: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    3.340289] hub 5-0:1.0: USB hub found
Jun  9 03:28:10 beartop kernel: [    3.340300] hub 5-0:1.0: 8 ports detected
Jun  9 03:28:10 beartop kernel: [    3.548465] ata_piix 0000:00:1f.2: version 2.12
Jun  9 03:28:10 beartop kernel: [    3.548494] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun  9 03:28:10 beartop kernel: [    3.548501] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jun  9 03:28:10 beartop kernel: [    3.548560] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    3.549523] scsi0 : ata_piix
Jun  9 03:28:10 beartop kernel: [    3.549654] scsi1 : ata_piix
Jun  9 03:28:10 beartop kernel: [    3.550861] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Jun  9 03:28:10 beartop kernel: [    3.550866] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Jun  9 03:28:10 beartop kernel: [    3.713463] ata1.00: ATA-8: WDC WD3200BJKT-00F4T0, 11.01A11, max UDMA/133
Jun  9 03:28:10 beartop kernel: [    3.713468] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
Jun  9 03:28:10 beartop kernel: [    3.721473] ata1.00: configured for UDMA/133
Jun  9 03:28:10 beartop kernel: [    3.736052] usb 2-1: device not accepting address 2, error -71
Jun  9 03:28:10 beartop kernel: [    3.792090] hub 2-0:1.0: unable to enumerate USB device on port 1
Jun  9 03:28:10 beartop kernel: [    3.884565] ata2.00: ATAPI: Optiarc DVD+/-RW AD-5560A, DD11, max UDMA/33
Jun  9 03:28:10 beartop kernel: [    3.900505] ata2.00: configured for UDMA/33
Jun  9 03:28:10 beartop kernel: [    3.900628] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BJKT-0 11.0 PQ: 0 ANSI: 5
Jun  9 03:28:10 beartop kernel: [    3.901783] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-5560A DD11 PQ: 0 ANSI: 5
Jun  9 03:28:10 beartop kernel: [    3.902282] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 03:28:10 beartop kernel: [    3.902299] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [    3.905233] usb 5-3: new high speed USB device using ehci_hcd and address 2
Jun  9 03:28:10 beartop kernel: [    3.964179] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Jun  9 03:28:10 beartop kernel: [    3.964223] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  9 03:28:10 beartop kernel: [    4.016977] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun  9 03:28:10 beartop kernel: [    4.021937] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  9 03:28:10 beartop kernel: [    4.084131] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Jun  9 03:28:10 beartop kernel: [    4.087255] b44.c:v2.0
Jun  9 03:28:10 beartop kernel: [    4.101882] usb 5-3: configuration #1 chosen from 1 choice
Jun  9 03:28:10 beartop kernel: [    4.108506] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:6f:eb:fd
Jun  9 03:28:10 beartop kernel: [    4.117610] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jun  9 03:28:10 beartop kernel: [    4.117663] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jun  9 03:28:10 beartop kernel: [    4.135714] usbcore: registered new interface driver libusual
Jun  9 03:28:10 beartop kernel: [    4.145968] Driver 'sd' needs updating - please use bus_type methods
Jun  9 03:28:10 beartop kernel: [    4.146113] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun  9 03:28:10 beartop kernel: [    4.146134] sd 0:0:0:0: [sda] Write Protect is off
Jun  9 03:28:10 beartop kernel: [    4.146137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  9 03:28:10 beartop kernel: [    4.146170] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 03:28:10 beartop kernel: [    4.146260] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun  9 03:28:10 beartop kernel: [    4.146279] sd 0:0:0:0: [sda] Write Protect is off
Jun  9 03:28:10 beartop kernel: [    4.146282] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  9 03:28:10 beartop kernel: [    4.146315] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 03:28:10 beartop kernel: [    4.146321]  sda:<6>Initializing USB Mass Storage driver...
Jun  9 03:28:10 beartop kernel: [    4.154100] scsi2 : SCSI emulation for USB Mass Storage devices
Jun  9 03:28:10 beartop kernel: [    4.154671] usb-storage: device found at 2
Jun  9 03:28:10 beartop kernel: [    4.154675] usb-storage: waiting for device to settle before scanning
Jun  9 03:28:10 beartop kernel: [    4.154695] usbcore: registered new interface driver usb-storage
Jun  9 03:28:10 beartop kernel: [    4.154700] USB Mass Storage support registered.
Jun  9 03:28:10 beartop kernel: [    4.165102] Driver 'sr' needs updating - please use bus_type methods
Jun  9 03:28:10 beartop kernel: [    4.176416]  sda1 sda2 < sda5 >
Jun  9 03:28:10 beartop kernel: [    4.200319] sd 0:0:0:0: [sda] Attached SCSI disk
Jun  9 03:28:10 beartop kernel: [    4.209090] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jun  9 03:28:10 beartop kernel: [    4.209096] Uniform CD-ROM driver Revision: 3.20
Jun  9 03:28:10 beartop kernel: [    4.209221] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun  9 03:28:10 beartop kernel: [    4.482235] PM: Starting manual resume from disk
Jun  9 03:28:10 beartop kernel: [    4.482241] PM: Resume from partition 8:5
Jun  9 03:28:10 beartop kernel: [    4.482243] PM: Checking hibernation image.
Jun  9 03:28:10 beartop kernel: [    4.482490] PM: Resume from disk failed.
Jun  9 03:28:10 beartop kernel: [    4.510292] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun  9 03:28:10 beartop kernel: [    4.510298] EXT3-fs: write access will be enabled during recovery.
Jun  9 03:28:10 beartop kernel: [    5.292189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc0002c0b6961]
Jun  9 03:28:10 beartop kernel: [    9.152322] usb-storage: device scan complete
Jun  9 03:28:10 beartop kernel: [    9.153128] scsi 2:0:0:0: Direct-Access     Simple   Bonzai Xpress    0.00 PQ: 0 ANSI: 2
Jun  9 03:28:10 beartop kernel: [    9.155212] sd 2:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:28:10 beartop kernel: [    9.155715] sd 2:0:0:0: [sdb] Write Protect is off
Jun  9 03:28:10 beartop kernel: [    9.155718] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:28:10 beartop kernel: [    9.155722] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:28:10 beartop kernel: [    9.157708] sd 2:0:0:0: [sdb] 8060927 512-byte hardware sectors (4127 MB)
Jun  9 03:28:10 beartop kernel: [    9.158294] sd 2:0:0:0: [sdb] Write Protect is off
Jun  9 03:28:10 beartop kernel: [    9.158297] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jun  9 03:28:10 beartop kernel: [    9.158300] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Jun  9 03:28:10 beartop kernel: [    9.158306]  sdb: sdb1
Jun  9 03:28:10 beartop kernel: [    9.263069] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Jun  9 03:28:10 beartop kernel: [    9.263217] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun  9 03:28:10 beartop kernel: [   11.965678] kjournald starting.  Commit interval 5 seconds
Jun  9 03:28:10 beartop kernel: [   11.965714] EXT3-fs: sda1: orphan cleanup on readonly fs
Jun  9 03:28:10 beartop kernel: [   11.965722] ext3_orphan_cleanup: deleting unreferenced inode 2236547

about 50 more errors like that

Jun  9 03:28:10 beartop kernel: [   12.045185] EXT3-fs: sda1: 58 orphan inodes deleted
Jun  9 03:28:10 beartop kernel: [   12.045187] EXT3-fs: recovery complete.
Jun  9 03:28:10 beartop kernel: [   12.179040] EXT3-fs: mounted filesystem with ordered data mode.
Jun  9 03:28:10 beartop kernel: [   17.160479] udevd version 124 started
Jun  9 03:28:10 beartop kernel: [   17.819811] iTCO_vendor_support: vendor-support=0
Jun  9 03:28:10 beartop kernel: [   18.000200] Linux agpgart interface v0.103
Jun  9 03:28:10 beartop kernel: [   18.084252] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Jun  9 03:28:10 beartop kernel: [   18.084588] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Jun  9 03:28:10 beartop kernel: [   18.102206] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jun  9 03:28:10 beartop kernel: [   18.201820] ACPI: Battery Slot [BAT0] (battery present)
Jun  9 03:28:10 beartop kernel: [   18.224155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  9 03:28:10 beartop kernel: [   18.380186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jun  9 03:28:10 beartop kernel: [   18.380356] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Jun  9 03:28:10 beartop kernel: [   18.380512] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun  9 03:28:10 beartop kernel: [   18.426388] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jun  9 03:28:10 beartop kernel: [   18.478895] ACPI: AC Adapter [AC] (on-line)
Jun  9 03:28:10 beartop kernel: [   18.517926] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Jun  9 03:28:10 beartop kernel: [   18.518422] ACPI: Lid Switch [LID]
Jun  9 03:28:10 beartop kernel: [   18.518490] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Jun  9 03:28:10 beartop kernel: [   18.540060] ACPI: Power Button (CM) [PBTN]
Jun  9 03:28:10 beartop kernel: [   18.540192] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Jun  9 03:28:10 beartop kernel: [   18.561190] ricoh-mmc: Ricoh MMC Controller disabling driver
Jun  9 03:28:10 beartop kernel: [   18.561194] ricoh-mmc: Copyright(c) Philip Langdale
Jun  9 03:28:10 beartop kernel: [   18.562502] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Jun  9 03:28:10 beartop kernel: [   18.562526] ricoh-mmc: Controller is now disabled.
Jun  9 03:28:10 beartop kernel: [   18.578440] ACPI: Sleep Button (CM) [SBTN]
Jun  9 03:28:10 beartop kernel: [   18.648242] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun  9 03:28:10 beartop kernel: [   18.772056] intel_rng: FWH not detected
Jun  9 03:28:10 beartop kernel: [   18.904676] ACPI: WMI: Mapper loaded
Jun  9 03:28:10 beartop kernel: [   18.930501] sdhci: Secure Digital Host Controller Interface driver
Jun  9 03:28:10 beartop kernel: [   18.930506] sdhci: Copyright(c) Pierre Ossman
Jun  9 03:28:10 beartop kernel: [   19.008958] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
Jun  9 03:28:10 beartop kernel: [   19.008983] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Jun  9 03:28:10 beartop kernel: [   19.012256] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Jun  9 03:28:10 beartop kernel: [   19.043044] acpi device:2a: registered as cooling_device2
Jun  9 03:28:10 beartop kernel: [   19.043507] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/input/input6
Jun  9 03:28:10 beartop kernel: [   19.076074] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Jun  9 03:28:10 beartop kernel: [   19.076298] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2c/input/input7
Jun  9 03:28:10 beartop kernel: [   19.099773] ieee80211_crypt: registered algorithm 'NULL'
Jun  9 03:28:10 beartop kernel: [   19.108027] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Jun  9 03:28:10 beartop kernel: [   19.370959] b44 0000:03:00.0: PCI INT A disabled
Jun  9 03:28:10 beartop kernel: [   19.389332] b43-pci-bridge 0000:0b:00.0: PCI INT A disabled
Jun  9 03:28:10 beartop kernel: [   19.433944] b44: Unknown symbol ssb_device_is_enabled
Jun  9 03:28:10 beartop kernel: [   19.434132] b44: Unknown symbol ssb_pcicore_dev_irqvecs_enable
Jun  9 03:28:10 beartop kernel: [   19.434372] b44: Unknown symbol ssb_bus_may_powerdown
Jun  9 03:28:10 beartop kernel: [   19.434498] b44: Unknown symbol ssb_dma_free_consistent
Jun  9 03:28:10 beartop kernel: [   19.434846] b44: Unknown symbol ssb_pcihost_register
Jun  9 03:28:10 beartop kernel: [   19.435189] b44: Unknown symbol ssb_dma_alloc_consistent
Jun  9 03:28:10 beartop kernel: [   19.435389] b44: Unknown symbol ssb_dma_set_mask
Jun  9 03:28:10 beartop kernel: [   19.435760] b44: Unknown symbol ssb_device_enable
Jun  9 03:28:10 beartop kernel: [   19.436180] b44: Unknown symbol ssb_driver_unregister
Jun  9 03:28:10 beartop kernel: [   19.436474] b44: Unknown symbol __ssb_driver_register
Jun  9 03:28:10 beartop kernel: [   19.436662] b44: Unknown symbol ssb_bus_powerup
Jun  9 03:28:10 beartop kernel: [   19.436870] b44: Unknown symbol generic_mii_ioctl
Jun  9 03:28:10 beartop kernel: [   19.437142] b44: Unknown symbol ssb_clockspeed
Jun  9 03:28:10 beartop kernel: [   19.437315] b44: Unknown symbol ssb_dma_translation
Jun  9 03:28:10 beartop kernel: [   19.486791] wl: module license 'unspecified' taints kernel.
Jun  9 03:28:10 beartop kernel: [   19.490450] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 03:28:10 beartop kernel: [   19.490475] wl 0000:0b:00.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [   19.542611] ieee80211_crypt: registered algorithm 'TKIP'
Jun  9 03:28:10 beartop kernel: [   19.542902] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.12
Jun  9 03:28:10 beartop kernel: [   19.640024] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  9 03:28:10 beartop kernel: [   19.676870] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Jun  9 03:28:10 beartop kernel: [   19.704130] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Jun  9 03:28:10 beartop kernel: [   19.704173] b44.c:v2.0
Jun  9 03:28:10 beartop kernel: [   19.729157] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:6f:eb:fd
Jun  9 03:28:10 beartop kernel: [   19.746765] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jun  9 03:28:10 beartop kernel: [   19.806907] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jun  9 03:28:10 beartop kernel: [   19.858427] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun  9 03:28:10 beartop kernel: [   19.858455] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  9 03:28:10 beartop kernel: [   20.906152] udev: renamed network interface eth1 to eth0
Jun  9 03:28:10 beartop kernel: [   20.937455] udev: renamed network interface eth0_rename to eth1
Jun  9 03:28:10 beartop kernel: [   22.144124] lp: driver loaded but no devices found
Jun  9 03:28:10 beartop kernel: [   22.309310] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k
Jun  9 03:28:10 beartop kernel: [   22.856857] EXT3 FS on sda1, internal journal
Jun  9 03:28:10 beartop kernel: [   23.765456] type=1505 audit(1244536088.787:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4241
Jun  9 03:28:10 beartop kernel: [   23.987172] type=1505 audit(1244536089.007:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4246
Jun  9 03:28:10 beartop kernel: [   23.987439] type=1505 audit(1244536089.007:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4246
Jun  9 03:28:10 beartop kernel: [   24.041455] type=1505 audit(1244536089.062:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4250
Jun  9 03:28:10 beartop kernel: [   24.194541] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun  9 03:28:10 beartop kernel: [   25.813694] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jun  9 03:28:10 beartop avahi-daemon[4859]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Jun  9 03:28:10 beartop avahi-daemon[4859]: Successfully dropped root privileges.
Jun  9 03:28:10 beartop avahi-daemon[4859]: avahi-daemon 0.6.23 starting up.
Jun  9 03:28:10 beartop avahi-daemon[4859]: Successfully called chroot().
Jun  9 03:28:10 beartop avahi-daemon[4859]: Successfully dropped remaining capabilities.
Jun  9 03:28:10 beartop avahi-daemon[4859]: No service file found in /etc/avahi/services.
Jun  9 03:28:10 beartop avahi-daemon[4859]: Network interface enumeration completed.
Jun  9 03:28:10 beartop avahi-daemon[4859]: Registering HINFO record with values 'I686'/'LINUX'.
Jun  9 03:28:10 beartop avahi-daemon[4859]: Server startup complete. Host name is beartop.local. Local service cookie is 3765865104.
Jun  9 03:28:11 beartop mysqld_safe[4959]: started
Jun  9 03:28:11 beartop mysqld[4962]: 090609  3:28:11  InnoDB: Started; log sequence number 0 43655
Jun  9 03:28:12 beartop mysqld[4962]: 090609  3:28:12 [Note] /usr/sbin/mysqld: ready for connections.
Jun  9 03:28:12 beartop mysqld[4962]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5001]: Upgrading MySQL tables if necessary.
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5007]: Looking for 'mysql' in: /usr/bin/mysql
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5007]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5007]: This installation of MySQL is already upgraded to 5.0.67, use --force if you still need to run mysql_upgrade
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5020]: Checking for insecure root accounts.
Jun  9 03:28:12 beartop kernel: [   27.904388] apm: BIOS not found.
Jun  9 03:28:12 beartop /etc/mysql/debian-start[5033]: Triggering myisam-recover for all MyISAM tables
Jun  9 03:28:13 beartop kernel: [   28.085889] ppdev: user-space parallel port driver
Jun  9 03:28:16 beartop kernel: [   31.332096] NET: Registered protocol family 10
Jun  9 03:28:16 beartop kernel: [   31.333351] lo: Disabled Privacy Extensions
Jun  9 03:28:16 beartop kernel: [   31.368925] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Jun  9 03:28:16 beartop kernel: [   31.368937] vboxdrv: Successfully done.
Jun  9 03:28:16 beartop kernel: [   31.368943] vboxdrv: Found 2 processor cores.
Jun  9 03:28:16 beartop kernel: [   31.369156] vboxdrv: fAsync=1 offMin=0xdb34d7c7 offMax=0xdb34d7c7
Jun  9 03:28:16 beartop kernel: [   31.369283] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Jun  9 03:28:16 beartop kernel: [   31.369296] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
Jun  9 03:28:17 beartop acpid: client connected from 5355[111:122] 
Jun  9 03:28:18 beartop bluetoothd[5419]: Bluetooth daemon
Jun  9 03:28:18 beartop kernel: [   33.226069] Bluetooth: Core ver 2.13
Jun  9 03:28:18 beartop kernel: [   33.227981] NET: Registered protocol family 31
Jun  9 03:28:18 beartop kernel: [   33.227992] Bluetooth: HCI device and connection manager initialized
Jun  9 03:28:18 beartop kernel: [   33.228001] Bluetooth: HCI socket layer initialized
Jun  9 03:28:18 beartop bluetoothd[5419]: Starting SDP server
Jun  9 03:28:18 beartop kernel: [   33.284175] Bluetooth: L2CAP ver 2.11
Jun  9 03:28:18 beartop kernel: [   33.284190] Bluetooth: L2CAP socket layer initialized
Jun  9 03:28:18 beartop bluetoothd[5419]: Starting experimental netlink support
Jun  9 03:28:18 beartop bluetoothd[5419]: Failed to find Bluetooth netlink family
Jun  9 03:28:18 beartop bluetoothd[5419]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Jun  9 03:28:18 beartop kernel: [   33.336046] Bluetooth: SCO (Voice Link) ver 0.6
Jun  9 03:28:18 beartop kernel: [   33.336058] Bluetooth: SCO socket layer initialized
Jun  9 03:28:18 beartop kernel: [   33.377336] Bluetooth: RFCOMM socket layer initialized
Jun  9 03:28:18 beartop kernel: [   33.377359] Bluetooth: RFCOMM TTY layer initialized
Jun  9 03:28:18 beartop kernel: [   33.377362] Bluetooth: RFCOMM ver 1.10
Jun  9 03:28:18 beartop kernel: [   33.381001] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  9 03:28:18 beartop kernel: [   33.381012] Bluetooth: BNEP filters: protocol multicast
Jun  9 03:28:18 beartop bluetoothd[5419]: bridge pan0 created
Jun  9 03:28:18 beartop kernel: [   33.424407] Bridge firewalling registered
Jun  9 03:28:18 beartop NetworkManager: <info>  starting... 
Jun  9 03:28:18 beartop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jun  9 03:28:18 beartop NetworkManager: <info>  eth0: driver is 'NULL(info.linux.driver)'. 
Jun  9 03:28:18 beartop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jun  9 03:28:18 beartop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_19_b9_6f_eb_fd 
Jun  9 03:28:18 beartop NetworkManager: <info>  eth1: driver is 'wl'. 
Jun  9 03:28:18 beartop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Jun  9 03:28:18 beartop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Jun  9 03:28:18 beartop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_19_7e_42_22_a1 
Jun  9 03:28:18 beartop NetworkManager: <info>  Trying to start the supplicant... 
Jun  9 03:28:18 beartop NetworkManager: <info>  Trying to start the system settings daemon... 
Jun  9 03:28:18 beartop NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: init!
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun  9 03:28:18 beartop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_19_b9_6f_eb_fd, iface: eth0): not well known
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_19_7e_42_22_a1, iface: eth1): not well known
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun  9 03:28:18 beartop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  9 03:28:18 beartop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: (137535776) ... get_connections.
Jun  9 03:28:18 beartop nm-system-settings:    SCPlugin-Ifupdown: (137535776) ... get_connections (managed=false): return empty list.
Jun  9 03:28:18 beartop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun  9 03:28:19 beartop avahi-daemon[4859]: Registering new address record for fe80::219:7eff:fe42:22a1 on eth1.*.
Jun  9 03:28:20 beartop acpid: client connected from 5531[0:0] 
Jun  9 03:28:20 beartop anacron[5565]: Anacron 2.3 started on 2009-06-09
Jun  9 03:28:20 beartop anacron[5565]: Normal exit (0 jobs run)
Jun  9 03:28:21 beartop /usr/sbin/cron[5608]: (CRON) INFO (pidfile fd = 3)
Jun  9 03:28:21 beartop /usr/sbin/cron[5609]: (CRON) STARTUP (fork ok)
Jun  9 03:28:21 beartop /usr/sbin/cron[5609]: (CRON) INFO (Running @reboot jobs)
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth0): bringing up device. 
Jun  9 03:28:22 beartop kernel: [   37.509487] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth0): preparing device. 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun  9 03:28:22 beartop kernel: [   37.513423] [drm] Initialized drm 1.1.0 20060810
Jun  9 03:28:22 beartop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun  9 03:28:22 beartop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth1): preparing device. 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jun  9 03:28:22 beartop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jun  9 03:28:22 beartop kernel: [   37.572135] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 03:28:22 beartop kernel: [   37.572157] pci 0000:00:02.0: setting latency timer to 64
Jun  9 03:28:22 beartop kernel: [   37.572477] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jun  9 03:28:22 beartop nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_19_b9_6f_eb_fd
Jun  9 03:28:22 beartop kernel: [   37.661337] NET: Registered protocol family 17
Jun  9 03:28:22 beartop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Jun  9 03:28:27 beartop gdmgreeter[5768]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jun  9 03:28:28 beartop kernel: [   43.572035] eth1: no IPv6 routers present
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) starting connection 'Auto Bearwork' 
Jun  9 03:28:47 beartop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun  9 03:28:47 beartop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Bearwork' requires no security.  No secrets needed. 
Jun  9 03:28:47 beartop NetworkManager: <info>  Config: added 'ssid' value 'Bearwork' 
Jun  9 03:28:47 beartop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jun  9 03:28:47 beartop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jun  9 03:28:47 beartop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun  9 03:28:47 beartop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jun  9 03:28:47 beartop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Jun  9 03:28:52 beartop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jun  9 03:28:57 beartop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jun  9 03:28:58 beartop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jun  9 03:28:58 beartop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Jun  9 03:28:58 beartop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Bearwork'. 
Jun  9 03:28:58 beartop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun  9 03:28:58 beartop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun  9 03:28:58 beartop NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jun  9 03:28:58 beartop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jun  9 03:28:58 beartop NetworkManager: <info>  dhclient started with pid 5795 
Jun  9 03:28:58 beartop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun  9 03:28:58 beartop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jun  9 03:28:58 beartop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jun  9 03:28:58 beartop dhclient: All rights reserved.
Jun  9 03:28:58 beartop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun  9 03:28:58 beartop dhclient: 
Jun  9 03:28:58 beartop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
Jun  9 03:28:58 beartop dhclient: Listening on LPF/eth1/00:19:7e:42:22:a1
Jun  9 03:28:58 beartop dhclient: Sending on   LPF/eth1/00:19:7e:42:22:a1
Jun  9 03:28:58 beartop dhclient: Sending on   Socket/fallback
Jun  9 03:28:59 beartop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun  9 03:29:00 beartop dhclient: DHCPOFFER of 192.168.1.200 from 192.168.1.100
Jun  9 03:29:00 beartop dhclient: DHCPREQUEST of 192.168.1.200 on eth1 to 255.255.255.255 port 67
Jun  9 03:29:00 beartop dhclient: DHCPACK of 192.168.1.200 from 192.168.1.100
Jun  9 03:29:00 beartop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jun  9 03:29:00 beartop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun  9 03:29:00 beartop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jun  9 03:29:00 beartop NetworkManager: <info>    address 192.168.1.200 
Jun  9 03:29:00 beartop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jun  9 03:29:00 beartop NetworkManager: <info>    gateway 192.168.1.100 
Jun  9 03:29:00 beartop NetworkManager: <info>    hostname 'beartop' 
Jun  9 03:29:00 beartop NetworkManager: <info>    nameserver '68.105.28.11' 
Jun  9 03:29:00 beartop NetworkManager: <info>    nameserver '68.105.29.11' 
Jun  9 03:29:00 beartop NetworkManager: <info>    nameserver '68.105.28.12' 
Jun  9 03:29:00 beartop NetworkManager: <info>    domain name 'ks.cox.net' 
Jun  9 03:29:00 beartop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun  9 03:29:00 beartop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jun  9 03:29:00 beartop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jun  9 03:29:00 beartop avahi-daemon[4859]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.200.
Jun  9 03:29:00 beartop avahi-daemon[4859]: New relevant interface eth1.IPv4 for mDNS.
Jun  9 03:29:00 beartop avahi-daemon[4859]: Registering new address record for 192.168.1.200 on eth1.IPv4.
Jun  9 03:29:00 beartop dhclient: bound to 192.168.1.200 -- renewal in 32991 seconds.
Jun  9 03:29:01 beartop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jun  9 03:29:01 beartop NetworkManager: <info>  Policy set 'Auto Bearwork' (eth1) as default for routing and DNS. 
Jun  9 03:29:01 beartop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jun  9 03:29:01 beartop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  9 03:29:02 beartop ntpdate[5851]: adjust time server 91.189.94.4 offset 0.175326 sec
Jun  9 03:29:32 beartop pulseaudio[5947]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jun  9 03:29:32 beartop pulseaudio[5949]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jun  9 03:29:32 beartop pulseaudio[5949]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jun  9 03:29:33 beartop x-session-manager[5889]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Jun  9 03:29:44 beartop x-session-manager[5889]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jun  9 03:29:51 beartop hald: mounted /dev/sdb1 on behalf of uid 1000
Jun  9 03:29:54 beartop x-session-manager[5889]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jun  9 03:29:55 beartop pulseaudio[5949]: module-x11-xsmp.c: X11 session manager not running.
Jun  9 03:29:55 beartop pulseaudio[5949]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jun  9 03:29:57 beartop anacron[6216]: Anacron 2.3 started on 2009-06-09
Jun  9 03:29:57 beartop anacron[6216]: Normal exit (0 jobs run)
Jun  9 03:29:57 beartop kernel: [  132.324723] CPU0 attaching NULL sched-domain.
Jun  9 03:29:57 beartop kernel: [  132.324737] CPU1 attaching NULL sched-domain.
Jun  9 03:29:57 beartop kernel: [  132.328196] CPU0 attaching sched-domain:
Jun  9 03:29:57 beartop kernel: [  132.328201]  domain 0: span 0-1 level MC
Jun  9 03:29:57 beartop kernel: [  132.328205]   groups: 0 1
Jun  9 03:29:57 beartop kernel: [  132.328211] CPU1 attaching sched-domain:
Jun  9 03:29:57 beartop kernel: [  132.328214]  domain 0: span 0-1 level MC
Jun  9 03:29:57 beartop kernel: [  132.328217]   groups: 1 0
Jun  9 03:32:02 beartop kernel: [  257.524073] CE: hpet increasing min_delta_ns to 15000 nsec
Jun  9 03:32:02 beartop kernel: [  257.524169] CE: hpet increasing min_delta_ns to 22500 nsec
Jun  9 03:32:02 beartop kernel: [  257.524263] CE: hpet increasing min_delta_ns to 33750 nsec
Jun  9 03:32:30 beartop kernel: [  285.258011] FAT: Filesystem panic (dev sdb1)
Jun  9 03:32:30 beartop kernel: [  285.258031]     invalid access to FAT (entry 0x30307474)
Jun  9 03:32:30 beartop kernel: [  285.258041]     File system has been set read-only
Jun  9 03:32:30 beartop kernel: [  285.263988] FAT: Filesystem panic (dev sdb1)
Jun  9 03:32:30 beartop kernel: [  285.264034]     invalid access to FAT (entry 0x3c2e7069)
Jun  9 03:32:32 beartop kernel: [  287.570581] FAT: Filesystem panic (dev sdb1)
Jun  9 03:32:32 beartop kernel: [  287.570595]     invalid access to FAT (entry 0x395bafb9)

there are about 100-200 more errors like that...

Jun  9 03:33:48 beartop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Jun  9 03:33:54 beartop kernel: [  369.893366] usb 5-3: USB disconnect, address 2
Jun  9 03:35:40 beartop kernel: [  475.037217] compiz.real[6049]: segfault at 3f38e3b0 ip 08055c7d sp bfdc6480 error 4 in compiz.real[8048000+34000]
Jun  9 03:35:42 beartop acpid: client 5531[0:0] has disconnected 
Jun  9 03:35:42 beartop acpid: client connected from 6731[0:0] 
Jun  9 03:35:47 beartop gdmgreeter[6751]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jun  9 03:35:52 beartop NetworkManager: <debug> [1244536552.824495] periodic_update(): Roamed from BSSID 00:1C:10:C0:88:23 (Bearwork) to (none) ((none)) 
Jun  9 03:35:55 beartop pulseaudio[6832]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jun  9 03:35:55 beartop pulseaudio[6834]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jun  9 03:35:55 beartop pulseaudio[6834]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jun  9 03:35:56 beartop x-session-manager[6775]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Jun  9 03:35:58 beartop NetworkManager: <debug> [1244536558.830437] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:10:C0:88:23 (Bearwork) 
Jun  9 03:36:06 beartop x-session-manager[6775]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jun  9 03:36:16 beartop x-session-manager[6775]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jun  9 03:36:16 beartop pulseaudio[6834]: module-x11-xsmp.c: X11 session manager not running.
Jun  9 03:36:16 beartop pulseaudio[6834]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jun  9 03:36:17 beartop anacron[7067]: Anacron 2.3 started on 2009-06-09
Jun  9 03:36:17 beartop anacron[7067]: Normal exit (0 jobs run)
Jun  9 03:36:17 beartop kernel: [  512.911963] CPU0 attaching NULL sched-domain.
Jun  9 03:36:17 beartop kernel: [  512.911978] CPU1 attaching NULL sched-domain.
Jun  9 03:36:17 beartop kernel: [  512.929343] CPU0 attaching sched-domain:
Jun  9 03:36:17 beartop kernel: [  512.929351]  domain 0: span 0-1 level MC
Jun  9 03:36:17 beartop kernel: [  512.929354]   groups: 0 1
Jun  9 03:36:17 beartop kernel: [  512.929362] CPU1 attaching sched-domain:
Jun  9 03:36:17 beartop kernel: [  512.929365]  domain 0: span 0-1 level MC
Jun  9 03:36:17 beartop kernel: [  512.929368]   groups: 1 0
Jun  9 03:39:01 beartop /USR/SBIN/CRON[7271]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun  9 03:39:52 beartop NetworkManager: <debug> [1244536792.946538] periodic_update(): Roamed from BSSID 00:1C:10:C0:88:23 (Bearwork) to (none) ((none)) 
Jun  9 03:39:58 beartop NetworkManager: <debug> [1244536798.950583] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:10:C0:88:23 (Bearwork) 
Jun  9 03:48:24 beartop kernel: [ 1239.592046] CE: hpet increasing min_delta_ns to 50624 nsec
Jun  9 04:06:42 beartop init: tty4 main process (4440) killed by TERM signal
Jun  9 04:06:42 beartop init: tty5 main process (4441) killed by TERM signal
Jun  9 04:06:42 beartop init: tty2 main process (4448) killed by TERM signal
Jun  9 04:06:42 beartop init: tty3 main process (4449) killed by TERM signal
Jun  9 04:06:42 beartop init: tty6 main process (4450) killed by TERM signal
Jun  9 04:06:42 beartop init: tty1 main process (5729) killed by TERM signal

---

### Post by bootdoc on 2009-06-20
Conflicker worm infects windows machines.  Mainly corporate networks.  VM's I believe could be considered a network.  I doubt this is the problem since linux and macs are not affected.

[http://www.guardian.co.uk/technology/2009/jan/19/downadup-conficker-kido-computer-infection](http://www.guardian.co.uk/technology/2009/jan/19/downadup-conficker-kido-computer-infection)

The worm can infect USB sticks and any corporate laptop that gets infected could then launch attacks if it was later connected to a home network.

---

