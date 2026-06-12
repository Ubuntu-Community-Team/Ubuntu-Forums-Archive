---
title: "Very Weird Ubuntu problems"
date: 2009-03-18
forum: General Help
---

### Post by mahasmb on 2009-03-18
Funny...

I **KNEW** that doing a fresh install wouldn't be a fix.

I had the following problem and someone suggested I do a fresh install: [http://ubuntuforums.org/showthread.php?t=880209](http://ubuntuforums.org/showthread.php?t=880209)

It's a few months later and I'm running Intrepid Ibex 8.10. It's a FRESH INSTALL with a CD straight from Canonical.

And I'm still having the same problems:
- After booting in with working internet, after a while my internet just disconnects and I can't see wireless networks anymore (thus I can't connect until I reboot)
- Sometimes when I boot into Ubuntu I have no working internet and I can't connect until I reboot.
- Some programs just freeze (firefox, Opera, Acidmax etc)
- Just now (I've had to reboot twice in 15 minutes), nearly everything froze and I couldn't even open terminal up or use the mouse to restart the computer. I had to press the button on my case to restart my computer.
- My sound just doesn't work, or the sound gets really messed up either right when I boot into Ubuntu or after a few hours of using Ubuntu. The only "fix" for this is rebooting again.

---

### Post by mahasmb on 2009-03-18
My system log file:

```
Mar 17 08:07:52 maha-desktop syslogd 1.5.0#2ubuntu6: restart.
Mar 17 08:07:52 maha-desktop anacron[12193]: Job `cron.daily' terminated
Mar 17 08:07:52 maha-desktop anacron[12193]: Normal exit (1 job run)
Mar 17 08:10:01 maha-desktop /USR/SBIN/CRON[15060]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:15:01 maha-desktop /USR/SBIN/CRON[15386]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:17:01 maha-desktop /USR/SBIN/CRON[15545]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 08:20:01 maha-desktop /USR/SBIN/CRON[15771]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:25:01 maha-desktop /USR/SBIN/CRON[16092]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:30:01 maha-desktop /USR/SBIN/CRON[16414]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:35:01 maha-desktop /USR/SBIN/CRON[16737]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:40:01 maha-desktop /USR/SBIN/CRON[17061]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:45:01 maha-desktop /USR/SBIN/CRON[17382]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:50:01 maha-desktop /USR/SBIN/CRON[17718]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 08:55:01 maha-desktop /USR/SBIN/CRON[18041]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:00:01 maha-desktop /USR/SBIN/CRON[18364]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:05:01 maha-desktop /USR/SBIN/CRON[18685]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:09:58 maha-desktop dhclient: DHCPREQUEST of 192.168.0.182 on wlan0 to 192.168.0.1 port 67
Mar 17 09:09:58 maha-desktop dhclient: DHCPACK of 192.168.0.182 from 192.168.0.1
Mar 17 09:09:58 maha-desktop dhclient: bound to 192.168.0.182 -- renewal in 36598 seconds.
Mar 17 09:10:01 maha-desktop /USR/SBIN/CRON[19016]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:15:01 maha-desktop /USR/SBIN/CRON[19342]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:17:01 maha-desktop /USR/SBIN/CRON[19492]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 09:20:01 maha-desktop /USR/SBIN/CRON[19714]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:25:01 maha-desktop /USR/SBIN/CRON[20014]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:30:01 maha-desktop /USR/SBIN/CRON[20335]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:35:01 maha-desktop /USR/SBIN/CRON[20659]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:40:01 maha-desktop /USR/SBIN/CRON[20980]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:45:01 maha-desktop /USR/SBIN/CRON[21304]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:50:01 maha-desktop /USR/SBIN/CRON[21639]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 09:55:02 maha-desktop /USR/SBIN/CRON[21964]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:00:01 maha-desktop /USR/SBIN/CRON[22287]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:05:01 maha-desktop /USR/SBIN/CRON[22608]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:10:01 maha-desktop /USR/SBIN/CRON[22929]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:15:01 maha-desktop /USR/SBIN/CRON[23255]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:17:01 maha-desktop /USR/SBIN/CRON[23405]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 10:20:01 maha-desktop /USR/SBIN/CRON[23627]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:25:01 maha-desktop /USR/SBIN/CRON[23927]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:30:01 maha-desktop /USR/SBIN/CRON[24225]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:35:01 maha-desktop /USR/SBIN/CRON[24549]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:40:01 maha-desktop /USR/SBIN/CRON[24870]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:45:01 maha-desktop /USR/SBIN/CRON[25192]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:50:01 maha-desktop /USR/SBIN/CRON[25530]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 10:55:01 maha-desktop /USR/SBIN/CRON[25832]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:00:01 maha-desktop /USR/SBIN/CRON[26153]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:05:01 maha-desktop /USR/SBIN/CRON[26476]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:10:01 maha-desktop /USR/SBIN/CRON[26797]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:13:08 maha-desktop kernel: [46878.578552] usb 4-2: new full speed USB device using uhci_hcd and address 11
Mar 17 11:13:08 maha-desktop kernel: [46878.755812] usb 4-2: configuration #1 chosen from 1 choice
Mar 17 11:15:01 maha-desktop /USR/SBIN/CRON[27269]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:17:01 maha-desktop /USR/SBIN/CRON[27423]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 11:20:01 maha-desktop /USR/SBIN/CRON[27660]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:25:01 maha-desktop /USR/SBIN/CRON[29419]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:30:01 maha-desktop /USR/SBIN/CRON[29743]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:35:01 maha-desktop /USR/SBIN/CRON[30070]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:40:01 maha-desktop /USR/SBIN/CRON[30398]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:45:01 maha-desktop /USR/SBIN/CRON[30724]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:50:01 maha-desktop /USR/SBIN/CRON[31052]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 11:55:01 maha-desktop /USR/SBIN/CRON[31395]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:00:01 maha-desktop /USR/SBIN/CRON[31733]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:05:01 maha-desktop /USR/SBIN/CRON[32115]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:10:02 maha-desktop /USR/SBIN/CRON[32416]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:15:01 maha-desktop /USR/SBIN/CRON[32744]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:17:01 maha-desktop /USR/SBIN/CRON[428]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 12:20:01 maha-desktop /USR/SBIN/CRON[639]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:25:01 maha-desktop /USR/SBIN/CRON[984]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:29:30 maha-desktop kernel: [51460.168054] usb 4-2: USB disconnect, address 11
Mar 17 12:29:44 maha-desktop kernel: [51474.648039] usb 1-5: new high speed USB device using ehci_hcd and address 7
Mar 17 12:29:44 maha-desktop kernel: [51474.781722] usb 1-5: configuration #1 chosen from 1 choice
Mar 17 12:29:45 maha-desktop kernel: [51475.098745] usbcore: registered new interface driver libusual
Mar 17 12:29:45 maha-desktop kernel: [51475.122428] Initializing USB Mass Storage driver...
Mar 17 12:29:45 maha-desktop kernel: [51475.124251] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 17 12:29:45 maha-desktop kernel: [51475.124472] usbcore: registered new interface driver usb-storage
Mar 17 12:29:45 maha-desktop kernel: [51475.124482] USB Mass Storage support registered.
Mar 17 12:29:45 maha-desktop kernel: [51475.126693] usb-storage: device found at 7
Mar 17 12:29:45 maha-desktop kernel: [51475.126701] usb-storage: waiting for device to settle before scanning
Mar 17 12:29:50 maha-desktop kernel: [51480.128361] usb-storage: device scan complete
Mar 17 12:29:50 maha-desktop kernel: [51480.130848] scsi 4:0:0:0: Direct-Access     SONY     "PSP" MS         1.00 PQ: 0 ANSI: 0 CCS
Mar 17 12:29:50 maha-desktop kernel: [51480.134944] sd 4:0:0:0: [sdc] 1964032 512-byte hardware sectors (1006 MB)
Mar 17 12:29:50 maha-desktop kernel: [51480.136086] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:29:50 maha-desktop kernel: [51480.136098] sd 4:0:0:0: [sdc] Mode Sense: 00 6a 20 00
Mar 17 12:29:50 maha-desktop kernel: [51480.136104] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:29:50 maha-desktop kernel: [51480.152950] sd 4:0:0:0: [sdc] 1964032 512-byte hardware sectors (1006 MB)
Mar 17 12:29:50 maha-desktop kernel: [51480.153571] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:29:50 maha-desktop kernel: [51480.153582] sd 4:0:0:0: [sdc] Mode Sense: 00 6a 20 00
Mar 17 12:29:50 maha-desktop kernel: [51480.153597] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:29:50 maha-desktop kernel: [51480.153608]  sdc: sdc1
Mar 17 12:29:50 maha-desktop kernel: [51480.156395] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Mar 17 12:29:50 maha-desktop kernel: [51480.157329] sd 4:0:0:0: Attached scsi generic sg4 type 0
Mar 17 12:29:53 maha-desktop hald: mounted /dev/sdc1 on behalf of uid 1000
Mar 17 12:30:01 maha-desktop /USR/SBIN/CRON[1441]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:32:46 maha-desktop kernel: [51656.933569] usb 1-5: USB disconnect, address 7
Mar 17 12:32:46 maha-desktop kernel: [51656.938584] Buffer I/O error on device sdc1, logical block 241
Mar 17 12:32:46 maha-desktop kernel: [51656.938602] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938622] Buffer I/O error on device sdc1, logical block 788
Mar 17 12:32:46 maha-desktop kernel: [51656.938628] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938635] Buffer I/O error on device sdc1, logical block 789
Mar 17 12:32:46 maha-desktop kernel: [51656.938640] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938647] Buffer I/O error on device sdc1, logical block 790
Mar 17 12:32:46 maha-desktop kernel: [51656.938654] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938662] Buffer I/O error on device sdc1, logical block 791
Mar 17 12:32:46 maha-desktop kernel: [51656.938667] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938674] Buffer I/O error on device sdc1, logical block 792
Mar 17 12:32:46 maha-desktop kernel: [51656.938680] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938686] Buffer I/O error on device sdc1, logical block 793
Mar 17 12:32:46 maha-desktop kernel: [51656.938692] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938699] Buffer I/O error on device sdc1, logical block 794
Mar 17 12:32:46 maha-desktop kernel: [51656.938705] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938712] Buffer I/O error on device sdc1, logical block 795
Mar 17 12:32:46 maha-desktop kernel: [51656.938717] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.938723] Buffer I/O error on device sdc1, logical block 796
Mar 17 12:32:46 maha-desktop kernel: [51656.938729] lost page write due to I/O error on sdc1
Mar 17 12:32:46 maha-desktop kernel: [51656.955641] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar 17 12:32:46 maha-desktop kernel: [51656.955658] end_request: I/O error, dev sdc, sector 850
Mar 17 12:32:47 maha-desktop kernel: [51657.021466] sd 4:0:0:0: [sdc] READ CAPACITY failed
Mar 17 12:32:47 maha-desktop kernel: [51657.021480] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar 17 12:32:47 maha-desktop kernel: [51657.021489] sd 4:0:0:0: [sdc] Sense not available.
Mar 17 12:32:47 maha-desktop kernel: [51657.021525] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:32:47 maha-desktop kernel: [51657.021532] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
Mar 17 12:32:47 maha-desktop kernel: [51657.021545] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:32:47 maha-desktop kernel: [51657.049036] sd 4:0:0:0: [sdc] READ CAPACITY failed
Mar 17 12:32:47 maha-desktop kernel: [51657.049048] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar 17 12:32:47 maha-desktop kernel: [51657.049058] sd 4:0:0:0: [sdc] Sense not available.
Mar 17 12:32:47 maha-desktop kernel: [51657.050387] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:32:47 maha-desktop kernel: [51657.050398] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
Mar 17 12:32:47 maha-desktop kernel: [51657.050403] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:32:47 maha-desktop kernel: [51657.054356] sd 4:0:0:0: [sdc] READ CAPACITY failed
Mar 17 12:32:47 maha-desktop kernel: [51657.054365] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar 17 12:32:47 maha-desktop kernel: [51657.054376] sd 4:0:0:0: [sdc] Sense not available.
Mar 17 12:32:47 maha-desktop kernel: [51657.056118] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:32:47 maha-desktop kernel: [51657.056126] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
Mar 17 12:32:47 maha-desktop kernel: [51657.056132] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:32:47 maha-desktop kernel: [51657.078676] sd 4:0:0:0: [sdc] READ CAPACITY failed
Mar 17 12:32:47 maha-desktop kernel: [51657.078697] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar 17 12:32:47 maha-desktop kernel: [51657.078705] sd 4:0:0:0: [sdc] Sense not available.
Mar 17 12:32:47 maha-desktop kernel: [51657.083118] sd 4:0:0:0: [sdc] Write Protect is off
Mar 17 12:32:47 maha-desktop kernel: [51657.083130] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
Mar 17 12:32:47 maha-desktop kernel: [51657.083136] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 17 12:32:47 maha-desktop hald[5598]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
Mar 17 12:32:47 maha-desktop hald: unmounted /dev/sdc1 from '/media/disk' on behalf of uid 0
Mar 17 12:35:01 maha-desktop /USR/SBIN/CRON[1897]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:40:01 maha-desktop /USR/SBIN/CRON[2223]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:45:01 maha-desktop /USR/SBIN/CRON[2609]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:48:53 maha-desktop kernel: [52623.355778] __ratelimit: 16 callbacks suppressed
Mar 17 12:48:53 maha-desktop kernel: [52623.355792] poweriso[2910]: segfault at 4f597d60 ip 08063f4a sp bfdf2340 error 4 in poweriso[8048000+9e000]
Mar 17 12:50:01 maha-desktop /USR/SBIN/CRON[2993]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:50:02 maha-desktop hald: unmounted /dev/scd0 from '/media/WINXP' on behalf of uid 1000
Mar 17 12:50:36 maha-desktop kernel: [52726.338953] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52726.338968] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:36 maha-desktop kernel: [52726.964643] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52726.964661] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:36 maha-desktop kernel: [52726.975725] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52726.975743] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:36 maha-desktop kernel: [52726.985688] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52726.985705] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:36 maha-desktop kernel: [52726.997939] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52726.997956] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:36 maha-desktop kernel: [52727.008201] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:36 maha-desktop kernel: [52727.008218] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:37 maha-desktop kernel: [52727.019455] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:37 maha-desktop kernel: [52727.019472] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:37 maha-desktop kernel: [52727.154201] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:37 maha-desktop kernel: [52727.154219] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:37 maha-desktop kernel: [52727.164992] end_request: I/O error, dev sr0, sector 1187456
Mar 17 12:50:37 maha-desktop kernel: [52727.165009] Buffer I/O error on device sr0, logical block 148432
Mar 17 12:50:37 maha-desktop kernel: [52727.786636] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 17 12:50:37 maha-desktop kernel: [52727.817165] ISOFS: changing to secondary root
Mar 17 12:50:37 maha-desktop hald: mounted /dev/scd0 on behalf of uid 1000
Mar 17 12:51:42 maha-desktop hald: unmounted /dev/scd0 from '/media/WINXP' on behalf of uid 1000
Mar 17 12:52:13 maha-desktop kernel: [52823.483456] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:52:13 maha-desktop kernel: [52823.585254] end_request: I/O error, dev sr0, sector 0
Mar 17 12:52:13 maha-desktop kernel: [52823.585271] Buffer I/O error on device sr0, logical block 0
Mar 17 12:52:13 maha-desktop kernel: [52823.588874] end_request: I/O error, dev sr0, sector 0
Mar 17 12:52:13 maha-desktop kernel: [52823.588892] Buffer I/O error on device sr0, logical block 0
Mar 17 12:53:04 maha-desktop kernel: [52874.814722] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:53:04 maha-desktop kernel: [52874.876948] end_request: I/O error, dev sr0, sector 0
Mar 17 12:53:04 maha-desktop kernel: [52874.876964] Buffer I/O error on device sr0, logical block 0
Mar 17 12:53:04 maha-desktop kernel: [52874.929055] end_request: I/O error, dev sr0, sector 0
Mar 17 12:53:04 maha-desktop kernel: [52874.929074] Buffer I/O error on device sr0, logical block 0
Mar 17 12:53:52 maha-desktop kernel: [52922.342661] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:53:52 maha-desktop kernel: [52922.591086] end_request: I/O error, dev sr0, sector 0
Mar 17 12:53:52 maha-desktop kernel: [52922.591100] Buffer I/O error on device sr0, logical block 0
Mar 17 12:53:52 maha-desktop kernel: [52922.594544] end_request: I/O error, dev sr0, sector 0
Mar 17 12:53:52 maha-desktop kernel: [52922.594560] Buffer I/O error on device sr0, logical block 0
Mar 17 12:54:24 maha-desktop kernel: [52954.787686] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:54:24 maha-desktop kernel: [52954.853553] end_request: I/O error, dev sr0, sector 0
Mar 17 12:54:24 maha-desktop kernel: [52954.853570] Buffer I/O error on device sr0, logical block 0
Mar 17 12:54:24 maha-desktop kernel: [52954.859424] end_request: I/O error, dev sr0, sector 0
Mar 17 12:54:24 maha-desktop kernel: [52954.859440] Buffer I/O error on device sr0, logical block 0
Mar 17 12:55:01 maha-desktop /USR/SBIN/CRON[3661]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 12:55:27 maha-desktop kernel: [53017.141305] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:55:27 maha-desktop kernel: [53017.179592] end_request: I/O error, dev sr0, sector 0
Mar 17 12:55:27 maha-desktop kernel: [53017.179613] Buffer I/O error on device sr0, logical block 0
Mar 17 12:55:27 maha-desktop kernel: [53017.182367] end_request: I/O error, dev sr0, sector 0
Mar 17 12:55:27 maha-desktop kernel: [53017.182385] Buffer I/O error on device sr0, logical block 0
Mar 17 12:56:05 maha-desktop kernel: [53055.155709] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:56:05 maha-desktop kernel: [53055.188823] end_request: I/O error, dev sr0, sector 0
Mar 17 12:56:05 maha-desktop kernel: [53055.188841] Buffer I/O error on device sr0, logical block 0
Mar 17 12:56:05 maha-desktop kernel: [53055.193398] end_request: I/O error, dev sr0, sector 0
Mar 17 12:56:05 maha-desktop kernel: [53055.193420] Buffer I/O error on device sr0, logical block 0
Mar 17 12:59:06 maha-desktop kernel: [53236.517716] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 12:59:06 maha-desktop kernel: [53236.724926] end_request: I/O error, dev sr0, sector 0
Mar 17 12:59:06 maha-desktop kernel: [53236.724943] Buffer I/O error on device sr0, logical block 0
Mar 17 12:59:06 maha-desktop kernel: [53236.730191] end_request: I/O error, dev sr0, sector 0
Mar 17 12:59:06 maha-desktop kernel: [53236.730206] Buffer I/O error on device sr0, logical block 0
Mar 17 13:00:01 maha-desktop /USR/SBIN/CRON[4196]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:01:53 maha-desktop kernel: [53404.007825] device wlan0 entered promiscuous mode
Mar 17 13:01:58 maha-desktop kernel: [53408.646825] device wlan0 left promiscuous mode
Mar 17 13:02:00 maha-desktop kernel: [53410.990418] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:00 maha-desktop kernel: [53410.990439] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:00 maha-desktop kernel: [53410.997355] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:00 maha-desktop kernel: [53410.997376] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:00 maha-desktop kernel: [53411.003977] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:00 maha-desktop kernel: [53411.003996] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:00 maha-desktop kernel: [53411.011111] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:00 maha-desktop kernel: [53411.011132] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.016281] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:01 maha-desktop kernel: [53411.016301] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.026529] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:01 maha-desktop kernel: [53411.026550] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.036800] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:01 maha-desktop kernel: [53411.036818] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.217675] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:01 maha-desktop kernel: [53411.217695] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.227233] end_request: I/O error, dev sr0, sector 1323464
Mar 17 13:02:01 maha-desktop kernel: [53411.227251] Buffer I/O error on device sr0, logical block 165433
Mar 17 13:02:01 maha-desktop kernel: [53411.757485] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 17 13:02:01 maha-desktop kernel: [53411.760924] ISOFS: changing to secondary root
Mar 17 13:02:01 maha-desktop hald: mounted /dev/scd0 on behalf of uid 1000
Mar 17 13:02:02 maha-desktop kernel: [53412.190328] usb 2-1.1: reset full speed USB device using uhci_hcd and address 3
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: HCI dev 0 registered
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: HCI dev 0 up
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Registered interface org.bluez.NetworkPeer on path /org/bluez/hci0
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Registered interface org.bluez.NetworkHub on path /org/bluez/hci0
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Registered interface org.bluez.NetworkRouter on path /org/bluez/hci0
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Registered interface org.bluez.Service on path /org/bluez/hci0
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Failed to listen on control channel
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/hci0
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Adapter /org/bluez/hci0 has been enabled
Mar 17 13:02:02 maha-desktop bluetoothd[5744]: Starting security manager 0
Mar 17 13:03:25 maha-desktop hald: unmounted /dev/scd0 from '/media/MP3 new 2' on behalf of uid 1000
Mar 17 13:04:51 maha-desktop kernel: [53581.146196] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 13:04:51 maha-desktop kernel: [53581.163424] end_request: I/O error, dev sr0, sector 0
Mar 17 13:04:51 maha-desktop kernel: [53581.163444] Buffer I/O error on device sr0, logical block 0
Mar 17 13:04:51 maha-desktop kernel: [53581.169744] end_request: I/O error, dev sr0, sector 0
Mar 17 13:04:51 maha-desktop kernel: [53581.169765] Buffer I/O error on device sr0, logical block 0
Mar 17 13:05:01 maha-desktop /USR/SBIN/CRON[4712]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:10:01 maha-desktop /USR/SBIN/CRON[5064]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:12:19 maha-desktop dnsmasq[5453]: reading /etc/resolv.conf
Mar 17 13:12:19 maha-desktop dnsmasq[5453]: using nameserver 192.168.0.1#53
Mar 17 13:12:37 maha-desktop kernel: [54047.261230] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:37 maha-desktop kernel: [54047.261244] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:37 maha-desktop kernel: [54047.576377] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:37 maha-desktop kernel: [54047.576391] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:37 maha-desktop kernel: [54047.759410] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:37 maha-desktop kernel: [54047.759424] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:37 maha-desktop kernel: [54047.935169] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:37 maha-desktop kernel: [54047.935188] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:38 maha-desktop kernel: [54048.110852] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:38 maha-desktop kernel: [54048.110865] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:38 maha-desktop kernel: [54048.286570] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:38 maha-desktop kernel: [54048.286585] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:38 maha-desktop kernel: [54048.469601] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:38 maha-desktop kernel: [54048.469619] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:38 maha-desktop kernel: [54048.747803] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:38 maha-desktop kernel: [54048.747820] Buffer I/O error on device sr0, logical block 150
Mar 17 13:12:38 maha-desktop kernel: [54048.930795] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:12:38 maha-desktop kernel: [54048.930808] Buffer I/O error on device sr0, logical block 150
Mar 17 13:15:01 maha-desktop /USR/SBIN/CRON[5421]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:17:01 maha-desktop /USR/SBIN/CRON[5592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 13:18:21 maha-desktop kernel: [54391.165323] end_request: I/O error, dev sr0, sector 0
Mar 17 13:18:21 maha-desktop kernel: [54391.165340] Buffer I/O error on device sr0, logical block 0
Mar 17 13:18:21 maha-desktop kernel: [54391.173076] end_request: I/O error, dev sr0, sector 0
Mar 17 13:18:21 maha-desktop kernel: [54391.173096] Buffer I/O error on device sr0, logical block 0
Mar 17 13:18:21 maha-desktop kernel: [54391.190948] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 13:20:01 maha-desktop /USR/SBIN/CRON[5939]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:23:58 maha-desktop kernel: [54728.240337] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:58 maha-desktop kernel: [54728.240350] Buffer I/O error on device sr0, logical block 150
Mar 17 13:23:58 maha-desktop kernel: [54728.573258] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:58 maha-desktop kernel: [54728.573276] Buffer I/O error on device sr0, logical block 150
Mar 17 13:23:58 maha-desktop kernel: [54728.906243] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:58 maha-desktop kernel: [54728.906260] Buffer I/O error on device sr0, logical block 150
Mar 17 13:23:59 maha-desktop kernel: [54729.239235] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:59 maha-desktop kernel: [54729.239250] Buffer I/O error on device sr0, logical block 150
Mar 17 13:23:59 maha-desktop kernel: [54729.572225] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:59 maha-desktop kernel: [54729.572239] Buffer I/O error on device sr0, logical block 150
Mar 17 13:23:59 maha-desktop kernel: [54729.905217] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:23:59 maha-desktop kernel: [54729.905230] Buffer I/O error on device sr0, logical block 150
Mar 17 13:24:00 maha-desktop kernel: [54730.238146] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:24:00 maha-desktop kernel: [54730.238159] Buffer I/O error on device sr0, logical block 150
Mar 17 13:24:00 maha-desktop kernel: [54730.756085] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:24:00 maha-desktop kernel: [54730.756098] Buffer I/O error on device sr0, logical block 150
Mar 17 13:24:01 maha-desktop kernel: [54731.089006] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:24:01 maha-desktop kernel: [54731.089019] Buffer I/O error on device sr0, logical block 150
Mar 17 13:24:16 maha-desktop hald: mounted /dev/sda1 on behalf of uid 1000
Mar 17 13:25:01 maha-desktop /USR/SBIN/CRON[6330]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 13:25:34 maha-desktop kernel: [54824.029367] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.029381] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:34 maha-desktop kernel: [54824.227664] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.227677] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:34 maha-desktop kernel: [54824.403328] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.403342] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:34 maha-desktop kernel: [54824.586226] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.586240] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:34 maha-desktop kernel: [54824.769131] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.769145] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:34 maha-desktop kernel: [54824.951972] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:34 maha-desktop kernel: [54824.951986] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:35 maha-desktop kernel: [54825.134837] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:35 maha-desktop kernel: [54825.134851] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:35 maha-desktop kernel: [54825.420108] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:35 maha-desktop kernel: [54825.420121] Buffer I/O error on device sr0, logical block 150
Mar 17 13:25:35 maha-desktop kernel: [54825.595666] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:25:35 maha-desktop kernel: [54825.595687] Buffer I/O error on device sr0, logical block 150
Mar 17 13:26:32 maha-desktop kernel: [54882.081491] end_request: I/O error, dev sr0, sector 0
Mar 17 13:26:32 maha-desktop kernel: [54882.081504] Buffer I/O error on device sr0, logical block 0
Mar 17 13:26:32 maha-desktop kernel: [54882.085032] end_request: I/O error, dev sr0, sector 0
Mar 17 13:26:32 maha-desktop kernel: [54882.085043] Buffer I/O error on device sr0, logical block 0
Mar 17 13:27:14 maha-desktop kernel: [54924.152726] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:14 maha-desktop kernel: [54924.152741] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:14 maha-desktop kernel: [54924.536493] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:14 maha-desktop kernel: [54924.536506] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:15 maha-desktop kernel: [54925.333583] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:15 maha-desktop kernel: [54925.333596] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:15 maha-desktop kernel: [54925.717338] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:15 maha-desktop kernel: [54925.717354] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:16 maha-desktop kernel: [54926.101118] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:16 maha-desktop kernel: [54926.101131] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:16 maha-desktop kernel: [54926.484917] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:16 maha-desktop kernel: [54926.484936] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:16 maha-desktop kernel: [54926.868641] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:16 maha-desktop kernel: [54926.868655] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:17 maha-desktop kernel: [54927.488615] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:17 maha-desktop kernel: [54927.488628] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:17 maha-desktop kernel: [54927.872415] end_request: I/O error, dev sr0, sector 1200
Mar 17 13:27:17 maha-desktop kernel: [54927.872429] Buffer I/O error on device sr0, logical block 150
Mar 17 13:27:42 maha-desktop kernel: [54952.164860] cdrom: This disc doesn't have any tracks I recognize!
Mar 17 13:27:42 maha-desktop kernel: [54952.187101] end_request: I/O error, dev sr0, sector 0
Mar 17 13:27:42 maha-desktop kernel: [54952.187119] Buffer I/O error on device sr0, logical block 0
Mar 17 13:27:42 maha-desktop kernel: [54952.192366] end_request: I/O error, dev sr0, sector 0
Mar 17 13:27:42 maha-desktop kernel: [54952.192385] Buffer I/O error on device sr0, logical block 0
Mar 17 13:29:20 maha-desktop kernel: [55050.441391] poweriso[6778]: segfault at 4f597d60 ip 08063f4a sp bfd6b2c0 error 4 in poweriso[8048000+9e000]
Mar 17 13:30:01 maha-desktop /USR/SBIN/CRON[6841]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 17:46:17 maha-desktop syslogd 1.5.0#2ubuntu6: restart.
Mar 17 17:46:17 maha-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar 17 17:46:17 maha-desktop kernel: Cannot find map file.
Mar 17 17:46:17 maha-desktop kernel: Loaded 67655 symbols from 88 modules.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] DMI 2.4 present.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] RAMDISK: 377a2000 - 37fefd91
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0014 (r0 P4M900)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: RSDT 7FEE3000, 0034 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: FACP 7FEE3080, 0074 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3100, 62D0 (r1 P4M900 AWRDACPI     1000 MSFT  3000000)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: HPET 7FEE94C0, 0038 (r1 P4M900 AWRDACPI 42302E31 AWRD       98)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: MCFG 7FEE9500, 003C (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: APIC 7FEE9400, 0090 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] 896MB LOWMEM available.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   low ram: 00000000 - 38000000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   bootmap 00011000 - 00018000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #4 [00377a2000 - 0037fefd91]          RAMDISK ==> [00377a2000 - 0037fefd91]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] found SMP MP-table at [c00f3d60] 000f3d60
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Zone PFN ranges:
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007fee0
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Movable zone start PFN for each node
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] On node 0 totalpages: 523887
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Mar 17 17:46:17 maha-desktop kernel: [    0.000000]   HighMem zone: 292034 pages, LIFO batch:31
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 5, version 3, address 0xfecc0000, GSI 24-47
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519281
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Kernel command line: root=UUID=fab527b5-514d-4898-9584-cd6a6f071a5c ro quiet splash 
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Initializing CPU#0
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] TSC: using PIT calibration value
Mar 17 17:46:17 maha-desktop kernel: [    0.000000] Detected 2999.875 MHz processor.
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] console [tty0] enabled
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Memory: 2061984k/2096000k available (2576k kernel code, 32852k reserved, 1165k data, 424k init, 1178496k highmem)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] virtual kernel memory layout:
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] hpet clockevent registered
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.75 BogoMIPS (lpj=11999500)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Security Framework initialized
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] using mwait in idle threads.
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Mar 17 17:46:17 maha-desktop kernel: [    0.018666] ACPI: Core revision 20080609
Mar 17 17:46:17 maha-desktop kernel: [    0.022423] ACPI: Checking initramfs for custom DSDT
Mar 17 17:46:17 maha-desktop kernel: [    0.372416] ENABLING IO-APIC IRQs
Mar 17 17:46:17 maha-desktop kernel: [    0.372607] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 17 17:46:17 maha-desktop kernel: [    0.413114] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Mar 17 17:46:17 maha-desktop kernel: [    0.416026] Booting processor 1/1 ip 6000
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Initializing CPU#1
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5999.82 BogoMIPS (lpj=11999651)
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Mar 17 17:46:17 maha-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 17 17:46:17 maha-desktop kernel: [    0.500434] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Mar 17 17:46:17 maha-desktop kernel: [    0.500463] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 17 17:46:17 maha-desktop kernel: [    0.504061] Brought up 2 CPUs
Mar 17 17:46:17 maha-desktop kernel: [    0.504067] Total of 2 processors activated (11999.57 BogoMIPS).
Mar 17 17:46:17 maha-desktop kernel: [    0.504092] CPU0 attaching sched-domain:
Mar 17 17:46:17 maha-desktop kernel: [    0.504097]  domain 0: span 0-1 level SIBLING
Mar 17 17:46:17 maha-desktop kernel: [    0.504100]   groups: 0 1
Mar 17 17:46:17 maha-desktop kernel: [    0.504109] CPU1 attaching sched-domain:
Mar 17 17:46:17 maha-desktop kernel: [    0.504112]  domain 0: span 0-1 level SIBLING
Mar 17 17:46:17 maha-desktop kernel: [    0.504116]   groups: 1 0
Mar 17 17:46:17 maha-desktop kernel: [    0.504215] net_namespace: 840 bytes
Mar 17 17:46:17 maha-desktop kernel: [    0.504215] Booting paravirtualized kernel on bare hardware
Mar 17 17:46:17 maha-desktop kernel: [    0.504422] Time: 17:45:55  Date: 03/17/09
Mar 17 17:46:17 maha-desktop kernel: [    0.504460] NET: Registered protocol family 16
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] EISA bus registered
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] ACPI: bus type pci registered
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] PCI: MCFG area at e0000000 reserved in E820
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] PCI: Using MMCONFIG for extended config space
Mar 17 17:46:17 maha-desktop kernel: [    0.504495] PCI: Using configuration type 1 for base access
Mar 17 17:46:17 maha-desktop kernel: [    0.509687] ACPI: EC: Look up EC in DSDT
Mar 17 17:46:17 maha-desktop kernel: [    0.527256] ACPI: Interpreter enabled
Mar 17 17:46:17 maha-desktop kernel: [    0.527263] ACPI: (supports S0 S1 S4 S5)
Mar 17 17:46:17 maha-desktop kernel: [    0.527288] ACPI: Using IOAPIC for interrupt routing
Mar 17 17:46:17 maha-desktop kernel: [    0.540600] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 17 17:46:17 maha-desktop kernel: [    0.540600] PCI: 0000:00:00.0 reg 10 32bit mmio: [d8000000, dfffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.540675] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.540682] pci 0000:00:02.0: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.540751] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.540757] pci 0000:00:03.0: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.540820] PCI: 0000:00:0f.0 reg 10 io port: [fc00, fc07]
Mar 17 17:46:17 maha-desktop kernel: [    0.540829] PCI: 0000:00:0f.0 reg 14 io port: [f800, f803]
Mar 17 17:46:17 maha-desktop kernel: [    0.540838] PCI: 0000:00:0f.0 reg 18 io port: [f400, f407]
Mar 17 17:46:17 maha-desktop kernel: [    0.540846] PCI: 0000:00:0f.0 reg 1c io port: [f000, f003]
Mar 17 17:46:17 maha-desktop kernel: [    0.540855] PCI: 0000:00:0f.0 reg 20 io port: [ec00, ec0f]
Mar 17 17:46:17 maha-desktop kernel: [    0.540864] PCI: 0000:00:0f.0 reg 24 io port: [e800, e8ff]
Mar 17 17:46:17 maha-desktop kernel: [    0.540945] PCI: 0000:00:0f.1 reg 20 io port: [e400, e40f]
Mar 17 17:46:17 maha-desktop kernel: [    0.541041] PCI: 0000:00:10.0 reg 20 io port: [e000, e01f]
Mar 17 17:46:17 maha-desktop kernel: [    0.541070] pci 0000:00:10.0: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541072] pci 0000:00:10.0: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541075] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541081] pci 0000:00:10.0: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.541137] PCI: 0000:00:10.1 reg 20 io port: [dc00, dc1f]
Mar 17 17:46:17 maha-desktop kernel: [    0.541166] pci 0000:00:10.1: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541169] pci 0000:00:10.1: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541171] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541177] pci 0000:00:10.1: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.541233] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
Mar 17 17:46:17 maha-desktop kernel: [    0.541262] pci 0000:00:10.2: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541264] pci 0000:00:10.2: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541267] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541272] pci 0000:00:10.2: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.541328] PCI: 0000:00:10.3 reg 20 io port: [d400, d41f]
Mar 17 17:46:17 maha-desktop kernel: [    0.541357] pci 0000:00:10.3: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541360] pci 0000:00:10.3: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541362] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541368] pci 0000:00:10.3: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.541402] PCI: 0000:00:10.4 reg 10 32bit mmio: [fdfff000, fdfff0ff]
Mar 17 17:46:17 maha-desktop kernel: [    0.541453] pci 0000:00:10.4: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541455] pci 0000:00:10.4: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541458] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541463] pci 0000:00:10.4: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.541662] PCI: 0000:00:12.0 reg 10 io port: [d000, d0ff]
Mar 17 17:46:17 maha-desktop kernel: [    0.541671] PCI: 0000:00:12.0 reg 14 32bit mmio: [fdffe000, fdffe0ff]
Mar 17 17:46:17 maha-desktop kernel: [    0.541718] pci 0000:00:12.0: supports D1
Mar 17 17:46:17 maha-desktop kernel: [    0.541720] pci 0000:00:12.0: supports D2
Mar 17 17:46:17 maha-desktop kernel: [    0.541723] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.541728] pci 0000:00:12.0: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.544062] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544068] PCI: bridge 0000:00:01.0 32bit mmio: [fdc00000, fdcfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544074] PCI: bridge 0000:00:01.0 32bit mmio pref: [fdb00000, fdbfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544124] PCI: 0000:02:00.0 reg 10 32bit mmio: [fa000000, faffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544139] PCI: 0000:02:00.0 reg 14 64bit mmio: [c0000000, cfffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544153] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544162] PCI: 0000:02:00.0 reg 24 io port: [bc00, bc7f]
Mar 17 17:46:17 maha-desktop kernel: [    0.544171] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544243] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544249] PCI: bridge 0000:00:02.0 32bit mmio: [f8000000, fbffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544257] PCI: bridge 0000:00:02.0 64bit mmio pref: [c0000000, cfffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544318] PCI: bridge 0000:00:03.0 io port: [a000, afff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544323] PCI: bridge 0000:00:03.0 32bit mmio: [fde00000, fdefffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544332] PCI: bridge 0000:00:03.0 64bit mmio pref: [fdd00000, fddfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544389] PCI: 0000:04:04.0 reg 10 32bit mmio: [fdaf0000, fdafffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544490] pci 0000:00:13.1: transparent bridge
Mar 17 17:46:17 maha-desktop kernel: [    0.544496] PCI: bridge 0000:00:13.1 io port: [9000, 9fff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544501] PCI: bridge 0000:00:13.1 32bit mmio: [fda00000, fdafffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544509] PCI: bridge 0000:00:13.1 64bit mmio pref: [fd900000, fd9fffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.544536] bus 00 -> node 0
Mar 17 17:46:17 maha-desktop kernel: [    0.544548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 17 17:46:17 maha-desktop kernel: [    0.545177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
Mar 17 17:46:17 maha-desktop kernel: [    0.545392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Mar 17 17:46:17 maha-desktop kernel: [    0.545609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
Mar 17 17:46:17 maha-desktop kernel: [    0.635212] ACPI: PCI Root Bridge [PCI1] (0000:80)
Mar 17 17:46:17 maha-desktop kernel: [    0.635212] PCI: 0000:80:01.0 reg 10 64bit mmio: [bfffc000, bfffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.636062] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
Mar 17 17:46:17 maha-desktop kernel: [    0.636068] pci 0000:80:01.0: PME# disabled
Mar 17 17:46:17 maha-desktop kernel: [    0.636117] bus 80 -> node 0
Mar 17 17:46:17 maha-desktop kernel: [    0.636127] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
Mar 17 17:46:17 maha-desktop kernel: [    0.636766] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Mar 17 17:46:17 maha-desktop kernel: [    0.636766] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Mar 17 17:46:17 maha-desktop kernel: [    0.637024] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
Mar 17 17:46:17 maha-desktop kernel: [    0.637355] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
Mar 17 17:46:17 maha-desktop kernel: [    0.637645] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 17 17:46:17 maha-desktop kernel: [    0.637926] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 17 17:46:17 maha-desktop kernel: [    0.638205] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 17 17:46:17 maha-desktop kernel: [    0.638509] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
Mar 17 17:46:17 maha-desktop kernel: [    0.638626] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 17 17:46:17 maha-desktop kernel: [    0.638626] pnp: PnP ACPI init
Mar 17 17:46:17 maha-desktop kernel: [    0.638626] ACPI: bus type pnp registered
Mar 17 17:46:17 maha-desktop kernel: [    0.648592] pnp: PnP ACPI: found 19 devices
Mar 17 17:46:17 maha-desktop kernel: [    0.648592] ACPI: ACPI bus type pnp unregistered
Mar 17 17:46:17 maha-desktop kernel: [    0.648592] PnPBIOS: Disabled by ACPI PNP
Mar 17 17:46:17 maha-desktop kernel: [    0.648592] PCI: Using ACPI for IRQ routing
Mar 17 17:46:17 maha-desktop kernel: [    0.652051] NET: Registered protocol family 8
Mar 17 17:46:17 maha-desktop kernel: [    0.652054] NET: Registered protocol family 20
Mar 17 17:46:17 maha-desktop kernel: [    0.652081] NetLabel: Initializing
Mar 17 17:46:17 maha-desktop kernel: [    0.652081] NetLabel:  domain hash size = 128
Mar 17 17:46:17 maha-desktop kernel: [    0.652081] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 17 17:46:17 maha-desktop kernel: [    0.652089] NetLabel:  unlabeled traffic allowed by default
Mar 17 17:46:17 maha-desktop kernel: [    0.652097] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
Mar 17 17:46:17 maha-desktop kernel: [    0.652106] hpet0: 3 32-bit timers, 14318180 Hz
Mar 17 17:46:17 maha-desktop kernel: [    0.654495] tracer: 772 pages allocated for 65536 entries of 48 bytes
Mar 17 17:46:17 maha-desktop kernel: [    0.654498]    actual entries 65620
Mar 17 17:46:17 maha-desktop kernel: [    0.654650] AppArmor: AppArmor Filesystem Enabled
Mar 17 17:46:17 maha-desktop kernel: [    0.654673] ACPI: RTC can wake from S4
Mar 17 17:46:17 maha-desktop kernel: [    0.656045] Switched to high resolution mode on CPU 0
Mar 17 17:46:17 maha-desktop kernel: [    0.656489] Switched to high resolution mode on CPU 1
Mar 17 17:46:17 maha-desktop kernel: [    0.656532] system 00:01: ioport range 0x400-0x47f has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656536] system 00:01: ioport range 0x500-0x50f has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656546] system 00:02: iomem range 0xf0001000-0xf0001fff has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656555] system 00:03: iomem range 0xf0002000-0xf0002fff has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656565] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656569] system 00:04: ioport range 0x800-0x805 has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656572] system 00:04: ioport range 0x290-0x297 has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656576] system 00:04: ioport range 0x880-0x88f has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656596] system 00:0f: iomem range 0xf0000000-0xf0000fff has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656605] system 00:10: iomem range 0xe0000000-0xefffffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656616] system 00:12: iomem range 0xf0000-0xfffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656621] system 00:12: iomem range 0xfe800000-0xfe8000ff has been reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656625] system 00:12: iomem range 0x7fee0000-0x7fefffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656629] system 00:12: iomem range 0xffff0000-0xffffffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656633] system 00:12: iomem range 0x0-0x9ffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656637] system 00:12: iomem range 0x100000-0x7fedffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656641] system 00:12: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656644] system 00:12: iomem range 0xfee00000-0xfee00fff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.656648] system 00:12: iomem range 0xfff80000-0xfffeffff could not be reserved
Mar 17 17:46:17 maha-desktop kernel: [    0.692243] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 17 17:46:17 maha-desktop kernel: [    0.692249] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Mar 17 17:46:17 maha-desktop kernel: [    0.692257] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfdcfffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692263] pci 0000:00:01.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692275] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
Mar 17 17:46:17 maha-desktop kernel: [    0.692279] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
Mar 17 17:46:17 maha-desktop kernel: [    0.692286] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692291] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692300] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
Mar 17 17:46:17 maha-desktop kernel: [    0.692304] pci 0000:00:03.0:   IO window: 0xa000-0xafff
Mar 17 17:46:17 maha-desktop kernel: [    0.692312] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692318] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692327] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
Mar 17 17:46:17 maha-desktop kernel: [    0.692332] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
Mar 17 17:46:17 maha-desktop kernel: [    0.692338] pci 0000:00:13.1:   MEM window: 0xfda00000-0xfdafffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692344] pci 0000:00:13.1:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Mar 17 17:46:17 maha-desktop kernel: [    0.692363] pci 0000:00:01.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    0.692381] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
Mar 17 17:46:17 maha-desktop kernel: [    0.692388] pci 0000:00:02.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    0.692401] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
Mar 17 17:46:17 maha-desktop kernel: [    0.692407] pci 0000:00:03.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    0.692416] pci 0000:00:13.1: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    0.692422] bus: 00 index 0 io port: [0, ffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692425] bus: 00 index 1 mmio: [0, ffffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692428] bus: 01 index 0 io port: [c000, cfff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692431] bus: 01 index 1 mmio: [fdc00000, fdcfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692434] bus: 01 index 2 mmio: [fdb00000, fdbfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692436] bus: 01 index 3 mmio: [0, 0]
Mar 17 17:46:17 maha-desktop kernel: [    0.692439] bus: 02 index 0 io port: [b000, bfff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692442] bus: 02 index 1 mmio: [f8000000, fbffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692445] bus: 02 index 2 mmio: [c0000000, cfffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692447] bus: 02 index 3 mmio: [0, 0]
Mar 17 17:46:17 maha-desktop kernel: [    0.692450] bus: 03 index 0 io port: [a000, afff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692453] bus: 03 index 1 mmio: [fde00000, fdefffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692455] bus: 03 index 2 mmio: [fdd00000, fddfffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692458] bus: 03 index 3 mmio: [0, 0]
Mar 17 17:46:17 maha-desktop kernel: [    0.692461] bus: 04 index 0 io port: [9000, 9fff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692464] bus: 04 index 1 mmio: [fda00000, fdafffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692466] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692469] bus: 04 index 3 io port: [0, ffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692472] bus: 04 index 4 mmio: [0, ffffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692475] bus: 80 index 0 io port: [0, ffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692477] bus: 80 index 1 mmio: [0, ffffffff]
Mar 17 17:46:17 maha-desktop kernel: [    0.692491] NET: Registered protocol family 2
Mar 17 17:46:17 maha-desktop kernel: [    0.704593] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.704981] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.705422] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    0.705705] TCP: Hash tables configured (established 131072 bind 65536)
Mar 17 17:46:17 maha-desktop kernel: [    0.705709] TCP reno registered
Mar 17 17:46:17 maha-desktop kernel: [    0.708643] NET: Registered protocol family 1
Mar 17 17:46:17 maha-desktop kernel: [    0.708807] checking if image is initramfs... it is
Mar 17 17:46:17 maha-desktop kernel: [    1.424392] Freeing initrd memory: 8503k freed
Mar 17 17:46:17 maha-desktop kernel: [    1.426230] audit: initializing netlink socket (disabled)
Mar 17 17:46:17 maha-desktop kernel: [    1.426251] type=2000 audit(1237311954.424:1): initialized
Mar 17 17:46:17 maha-desktop kernel: [    1.432159] highmem bounce pool size: 64 pages
Mar 17 17:46:17 maha-desktop kernel: [    1.432169] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 17 17:46:17 maha-desktop kernel: [    1.435941] VFS: Disk quotas dquot_6.5.1
Mar 17 17:46:17 maha-desktop kernel: [    1.436087] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 17 17:46:17 maha-desktop kernel: [    1.436246] msgmni has been set to 1743
Mar 17 17:46:17 maha-desktop kernel: [    1.436439] io scheduler noop registered
Mar 17 17:46:17 maha-desktop kernel: [    1.436443] io scheduler anticipatory registered
Mar 17 17:46:17 maha-desktop kernel: [    1.436445] io scheduler deadline registered
Mar 17 17:46:17 maha-desktop kernel: [    1.436461] io scheduler cfq registered (default)
Mar 17 17:46:17 maha-desktop kernel: [    1.436487] PCI: VIA PCI bridge detected.Disabling DAC.
Mar 17 17:46:17 maha-desktop kernel: [    1.436614] pci 0000:02:00.0: Boot video device
Mar 17 17:46:17 maha-desktop kernel: [    1.436829] pcieport-driver 0000:00:02.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    1.436882] pcieport-driver 0000:00:02.0: found MSI capability
Mar 17 17:46:17 maha-desktop kernel: [    1.436944] pci_express 0000:00:02.0:pcie00: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437031] pci_express 0000:00:02.0:pcie01: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437108] pci_express 0000:00:02.0:pcie02: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437180] pci_express 0000:00:02.0:pcie03: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437319] pcieport-driver 0000:00:03.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [    1.437377] pcieport-driver 0000:00:03.0: found MSI capability
Mar 17 17:46:17 maha-desktop kernel: [    1.437443] pci_express 0000:00:03.0:pcie00: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437519] pci_express 0000:00:03.0:pcie01: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437590] pci_express 0000:00:03.0:pcie02: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.437670] pci_express 0000:00:03.0:pcie03: allocate port service
Mar 17 17:46:17 maha-desktop kernel: [    1.443195] aer 0000:00:02.0:pcie01: service driver aer loaded
Mar 17 17:46:17 maha-desktop kernel: [    1.448582] aer 0000:00:03.0:pcie01: service driver aer loaded
Mar 17 17:46:17 maha-desktop kernel: [    1.448969] isapnp: Scanning for PnP cards...
Mar 17 17:46:17 maha-desktop kernel: [    1.803062] isapnp: No Plug & Play device found
Mar 17 17:46:17 maha-desktop kernel: [    1.865596] hpet_resources: 0xfe800000 is busy
Mar 17 17:46:17 maha-desktop kernel: [    1.865697] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 17 17:46:17 maha-desktop kernel: [    1.865859] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 17 17:46:17 maha-desktop kernel: [    1.866942] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 17 17:46:17 maha-desktop kernel: [    1.870317] brd: module loaded
Mar 17 17:46:17 maha-desktop kernel: [    1.870439] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 17 17:46:17 maha-desktop kernel: [    1.870674] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 17 17:46:17 maha-desktop kernel: [    1.871149] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 17 17:46:17 maha-desktop kernel: [    1.871158] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 17 17:46:17 maha-desktop kernel: [    1.872205] mice: PS/2 mouse device common for all mice
Mar 17 17:46:17 maha-desktop kernel: [    1.872440] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar 17 17:46:17 maha-desktop kernel: [    1.872481] rtc0: alarms up to one year, y3k, hpet irqs
Mar 17 17:46:17 maha-desktop kernel: [    1.872734] EISA: Probing bus 0 at eisa.0
Mar 17 17:46:17 maha-desktop kernel: [    1.872785] EISA: Detected 0 cards.
Mar 17 17:46:17 maha-desktop kernel: [    1.872790] cpuidle: using governor ladder
Mar 17 17:46:17 maha-desktop kernel: [    1.872793] cpuidle: using governor menu
Mar 17 17:46:17 maha-desktop kernel: [    1.873653] TCP cubic registered
Mar 17 17:46:17 maha-desktop kernel: [    1.873692] Using IPI No-Shortcut mode
Mar 17 17:46:17 maha-desktop kernel: [    1.874026] registered taskstats version 1
Mar 17 17:46:17 maha-desktop kernel: [    1.874214]   Magic number: 1:298:795
Mar 17 17:46:17 maha-desktop kernel: [    1.874290] tty ptyr3: hash matches
Mar 17 17:46:17 maha-desktop kernel: [    1.874382] rtc_cmos 00:07: setting system clock to 2009-03-17 17:45:56 UTC (1237311956)
Mar 17 17:46:17 maha-desktop kernel: [    1.874387] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 17 17:46:17 maha-desktop kernel: [    1.874389] EDD information not available.
Mar 17 17:46:17 maha-desktop kernel: [    1.874686] Freeing unused kernel memory: 424k freed
Mar 17 17:46:17 maha-desktop kernel: [    1.874752] Write protecting the kernel text: 2580k
Mar 17 17:46:17 maha-desktop kernel: [    1.874791] Write protecting the kernel read-only data: 940k
Mar 17 17:46:17 maha-desktop kernel: [    1.892575] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 17 17:46:17 maha-desktop kernel: [    2.102086] fuse init (API version 7.9)
Mar 17 17:46:17 maha-desktop kernel: [    2.196543] fan PNP0C0B:00: registered as cooling_device0
Mar 17 17:46:17 maha-desktop kernel: [    2.196556] ACPI: Fan [FAN] (on)
Mar 17 17:46:17 maha-desktop kernel: [    2.236582] processor ACPI0007:00: registered as cooling_device1
Mar 17 17:46:17 maha-desktop kernel: [    2.240544] processor ACPI0007:01: registered as cooling_device2
Mar 17 17:46:17 maha-desktop kernel: [    2.260566] thermal LNXTHERM:01: registered as thermal_zone0
Mar 17 17:46:17 maha-desktop kernel: [    2.261193] ACPI: Thermal Zone [THRM] (50 C)
Mar 17 17:46:17 maha-desktop kernel: [    2.312545] device-mapper: uevent: version 1.0.3
Mar 17 17:46:17 maha-desktop kernel: [    2.312895] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Mar 17 17:46:17 maha-desktop kernel: [    3.345851] No dock devices found.
Mar 17 17:46:17 maha-desktop kernel: [    3.390698] SCSI subsystem initialized
Mar 17 17:46:17 maha-desktop kernel: [    3.425432] libata version 3.00 loaded.
Mar 17 17:46:17 maha-desktop kernel: [    3.431306] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 17 17:46:17 maha-desktop kernel: [    3.431371] pata_acpi 0000:00:0f.0: PCI INT B disabled
Mar 17 17:46:17 maha-desktop kernel: [    3.444949] sata_via 0000:00:0f.0: version 2.3
Mar 17 17:46:17 maha-desktop kernel: [    3.444972] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 17 17:46:17 maha-desktop kernel: [    3.445019] sata_via 0000:00:0f.0: routed to hard irq line 11
Mar 17 17:46:17 maha-desktop kernel: [    3.445116] scsi0 : sata_via
Mar 17 17:46:17 maha-desktop kernel: [    3.445812] scsi1 : sata_via
Mar 17 17:46:17 maha-desktop kernel: [    3.450527] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
Mar 17 17:46:17 maha-desktop kernel: [    3.450536] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
Mar 17 17:46:17 maha-desktop kernel: [    3.545554] usbcore: registered new interface driver usbfs
Mar 17 17:46:17 maha-desktop kernel: [    3.545613] usbcore: registered new interface driver hub
Mar 17 17:46:17 maha-desktop kernel: [    3.546346] usbcore: registered new device driver usb
Mar 17 17:46:17 maha-desktop kernel: [    3.572174] USB Universal Host Controller Interface driver v3.0
Mar 17 17:46:17 maha-desktop kernel: [    3.628810] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Mar 17 17:46:17 maha-desktop kernel: [    3.628821] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Mar 17 17:46:17 maha-desktop kernel: [    3.652559] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar 17 17:46:17 maha-desktop kernel: [    3.856536] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar 17 17:46:17 maha-desktop kernel: [    3.857369] pata_via 0000:00:0f.1: version 0.3.3
Mar 17 17:46:17 maha-desktop kernel: [    3.858221] scsi2 : pata_via
Mar 17 17:46:17 maha-desktop kernel: [    3.858432] scsi3 : pata_via
Mar 17 17:46:17 maha-desktop kernel: [    3.863854] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
Mar 17 17:46:17 maha-desktop kernel: [    3.863864] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
Mar 17 17:46:17 maha-desktop kernel: [    4.037207] ata3.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
Mar 17 17:46:17 maha-desktop kernel: [    4.037216] ata3.00: 240121728 sectors, multi 16: LBA 
Mar 17 17:46:17 maha-desktop kernel: [    4.060129] ata3.01: ATA-8: WDC WD5000AAKB-00YSA0, 12.01C02, max UDMA/100
Mar 17 17:46:17 maha-desktop kernel: [    4.060137] ata3.01: 976773168 sectors, multi 16: LBA48 
Mar 17 17:46:17 maha-desktop kernel: [    4.077009] ata3.00: configured for UDMA/133
Mar 17 17:46:17 maha-desktop kernel: [    4.093888] ata3.01: configured for UDMA/100
Mar 17 17:46:17 maha-desktop kernel: [    4.269261] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
Mar 17 17:46:17 maha-desktop kernel: [    4.269314] ata4.01: ATAPI: CD-ROM CDU701-F, 1.0r, max MWDMA2
Mar 17 17:46:17 maha-desktop kernel: [    4.284286] ata4.00: configured for UDMA/33
Mar 17 17:46:17 maha-desktop kernel: [    4.300264] ata4.01: configured for MWDMA2
Mar 17 17:46:17 maha-desktop kernel: [    4.300439] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
Mar 17 17:46:17 maha-desktop kernel: [    4.300679] scsi 2:0:0:0: Attached scsi generic sg0 type 0
Mar 17 17:46:17 maha-desktop kernel: [    4.300785] scsi 2:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 12.0 PQ: 0 ANSI: 5
Mar 17 17:46:17 maha-desktop kernel: [    4.300907] scsi 2:0:1:0: Attached scsi generic sg1 type 0
Mar 17 17:46:17 maha-desktop kernel: [    4.304607] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
Mar 17 17:46:17 maha-desktop kernel: [    4.304756] scsi 3:0:0:0: Attached scsi generic sg2 type 5
Mar 17 17:46:17 maha-desktop kernel: [    4.305637] scsi 3:0:1:0: CD-ROM            SONY     CD-ROM CDU701-F  1.0r PQ: 0 ANSI: 5
Mar 17 17:46:17 maha-desktop kernel: [    4.305783] scsi 3:0:1:0: Attached scsi generic sg3 type 5
Mar 17 17:46:17 maha-desktop kernel: [    4.305891] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar 17 17:46:17 maha-desktop kernel: [    4.305911] uhci_hcd 0000:00:10.0: UHCI Host Controller
Mar 17 17:46:17 maha-desktop kernel: [    4.305989] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Mar 17 17:46:17 maha-desktop kernel: [    4.306034] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
Mar 17 17:46:17 maha-desktop kernel: [    4.306234] usb usb1: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    4.306298] hub 1-0:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    4.306314] hub 1-0:1.0: 2 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    4.513800] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Mar 17 17:46:17 maha-desktop kernel: [    4.513818] uhci_hcd 0000:00:10.1: UHCI Host Controller
Mar 17 17:46:17 maha-desktop kernel: [    4.513874] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Mar 17 17:46:17 maha-desktop kernel: [    4.513909] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
Mar 17 17:46:17 maha-desktop kernel: [    4.514089] usb usb2: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    4.514130] hub 2-0:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    4.514142] hub 2-0:1.0: 2 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    4.624020] usb 1-1: new full speed USB device using uhci_hcd and address 2
Mar 17 17:46:17 maha-desktop kernel: [    4.720732] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Mar 17 17:46:17 maha-desktop kernel: [    4.720745] uhci_hcd 0000:00:10.2: UHCI Host Controller
Mar 17 17:46:17 maha-desktop kernel: [    4.720795] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Mar 17 17:46:17 maha-desktop kernel: [    4.720823] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
Mar 17 17:46:17 maha-desktop kernel: [    4.720964] usb usb3: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    4.721005] hub 3-0:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    4.721017] hub 3-0:1.0: 2 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    4.792501] usb 1-1: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    4.795342] hub 1-1:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    4.797103] hub 1-1:1.0: 3 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    4.928745] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Mar 17 17:46:17 maha-desktop kernel: [    4.928757] uhci_hcd 0000:00:10.3: UHCI Host Controller
Mar 17 17:46:17 maha-desktop kernel: [    4.928803] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Mar 17 17:46:17 maha-desktop kernel: [    4.928838] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
Mar 17 17:46:17 maha-desktop kernel: [    4.928978] usb usb4: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    4.929019] hub 4-0:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    4.929031] hub 4-0:1.0: 2 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    5.085113] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
Mar 17 17:46:17 maha-desktop kernel: [    5.136276] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Mar 17 17:46:17 maha-desktop kernel: [    5.136300] ehci_hcd 0000:00:10.4: EHCI Host Controller
Mar 17 17:46:17 maha-desktop kernel: [    5.136360] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Mar 17 17:46:17 maha-desktop kernel: [    5.136417] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
Mar 17 17:46:17 maha-desktop kernel: [    5.172021] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 17 17:46:17 maha-desktop kernel: [    5.172206] usb usb5: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    5.172249] hub 5-0:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    5.172262] hub 5-0:1.0: 8 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    5.381015] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 17 17:46:17 maha-desktop kernel: [    5.385714] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:7b:51:0c, IRQ 23.
Mar 17 17:46:17 maha-desktop kernel: [    5.386425] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
Mar 17 17:46:17 maha-desktop kernel: [    5.525783] Driver 'sr' needs updating - please use bus_type methods
Mar 17 17:46:17 maha-desktop kernel: [    5.531980] Driver 'sd' needs updating - please use bus_type methods
Mar 17 17:46:17 maha-desktop kernel: [    5.532142] sd 2:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Mar 17 17:46:17 maha-desktop kernel: [    5.532179] sd 2:0:0:0: [sda] Write Protect is off
Mar 17 17:46:17 maha-desktop kernel: [    5.532185] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 17 17:46:17 maha-desktop kernel: [    5.532249] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 17:46:17 maha-desktop kernel: [    5.532415] sd 2:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Mar 17 17:46:17 maha-desktop kernel: [    5.532453] sd 2:0:0:0: [sda] Write Protect is off
Mar 17 17:46:17 maha-desktop kernel: [    5.532459] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 17 17:46:17 maha-desktop kernel: [    5.532547] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 17:46:17 maha-desktop kernel: [    5.532558]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 17 17:46:17 maha-desktop kernel: [    5.539054] Uniform CD-ROM driver Revision: 3.20
Mar 17 17:46:17 maha-desktop kernel: [    5.539188] sr 3:0:0:0: Attached scsi CD-ROM sr0
Mar 17 17:46:17 maha-desktop kernel: [    5.541785] sr1: scsi3-mmc drive: 14x/32x cd/rw xa/form2 cdda tray
Mar 17 17:46:17 maha-desktop kernel: [    5.541919] sr 3:0:1:0: Attached scsi CD-ROM sr1
Mar 17 17:46:17 maha-desktop kernel: [    5.553917]  sda1
Mar 17 17:46:17 maha-desktop kernel: [    5.554139] sd 2:0:0:0: [sda] Attached SCSI disk
Mar 17 17:46:17 maha-desktop kernel: [    5.554293] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Mar 17 17:46:17 maha-desktop kernel: [    5.554329] sd 2:0:1:0: [sdb] Write Protect is off
Mar 17 17:46:17 maha-desktop kernel: [    5.554335] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Mar 17 17:46:17 maha-desktop kernel: [    5.554400] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 17:46:17 maha-desktop kernel: [    5.554523] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Mar 17 17:46:17 maha-desktop kernel: [    5.554557] sd 2:0:1:0: [sdb] Write Protect is off
Mar 17 17:46:17 maha-desktop kernel: [    5.554562] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Mar 17 17:46:17 maha-desktop kernel: [    5.554619] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 17:46:17 maha-desktop kernel: [    5.554627]  sdb: sdb1 sdb2 sdb3 sdb4
Mar 17 17:46:17 maha-desktop kernel: [    5.569516] sd 2:0:1:0: [sdb] Attached SCSI disk
Mar 17 17:46:17 maha-desktop kernel: [    5.572111] usb 1-1.1: device not accepting address 3, error -71
Mar 17 17:46:17 maha-desktop kernel: [    5.605180] hub 1-1:1.0: cannot disable port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.607141] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.608136] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.608551] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.609133] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.610183] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.610191] hub 1-1:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Mar 17 17:46:17 maha-desktop kernel: [    5.611133] hub 1-1:1.0: cannot disable port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.612133] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.613136] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.614294] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.615131] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.616131] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.616139] hub 1-1:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Mar 17 17:46:17 maha-desktop kernel: [    5.617136] hub 1-1:1.0: cannot disable port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.618130] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.619132] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.620139] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.621765] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.622142] hub 1-1:1.0: cannot reset port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.622150] hub 1-1:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Mar 17 17:46:17 maha-desktop kernel: [    5.623135] hub 1-1:1.0: cannot disable port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.623150] hub 1-1:1.0: unable to enumerate USB device on port 1
Mar 17 17:46:17 maha-desktop kernel: [    5.624133] hub 1-1:1.0: cannot disable port 1 (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.625135] hub 1-1:1.0: hub_port_status failed (err = -71)
Mar 17 17:46:17 maha-desktop kernel: [    5.625167] usb 1-1: USB disconnect, address 2
Mar 17 17:46:17 maha-desktop kernel: [    6.036488] PM: Starting manual resume from disk
Mar 17 17:46:17 maha-desktop kernel: [    6.036494] PM: Resume from partition 8:19
Mar 17 17:46:17 maha-desktop kernel: [    6.036497] PM: Checking hibernation image.
Mar 17 17:46:17 maha-desktop kernel: [    6.036728] PM: Resume from disk failed.
Mar 17 17:46:17 maha-desktop kernel: [    6.091825] kjournald starting.  Commit interval 5 seconds
Mar 17 17:46:17 maha-desktop kernel: [    6.091835] EXT3-fs: sdb2: orphan cleanup on readonly fs
Mar 17 17:46:17 maha-desktop kernel: [    6.105405] ext3_orphan_cleanup: deleting unreferenced inode 557143
Mar 17 17:46:17 maha-desktop kernel: [    6.108026] usb 1-1: new full speed USB device using uhci_hcd and address 7
Mar 17 17:46:17 maha-desktop kernel: [    6.113758] ext3_orphan_cleanup: deleting unreferenced inode 82359
Mar 17 17:46:17 maha-desktop kernel: [    6.114218] ext3_orphan_cleanup: deleting unreferenced inode 557104
Mar 17 17:46:17 maha-desktop kernel: [    6.136487] ext3_orphan_cleanup: deleting unreferenced inode 5128447
Mar 17 17:46:17 maha-desktop kernel: [    6.144235] ext3_orphan_cleanup: deleting unreferenced inode 557077
Mar 17 17:46:17 maha-desktop kernel: [    6.144250] EXT3-fs: sdb2: 5 orphan inodes deleted
Mar 17 17:46:17 maha-desktop kernel: [    6.144254] EXT3-fs: recovery complete.
Mar 17 17:46:17 maha-desktop kernel: [    6.175272] EXT3-fs: mounted filesystem with ordered data mode.
Mar 17 17:46:17 maha-desktop kernel: [    6.285343] usb 1-1: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [    6.288177] hub 1-1:1.0: USB hub found
Mar 17 17:46:17 maha-desktop kernel: [    6.290144] hub 1-1:1.0: 3 ports detected
Mar 17 17:46:17 maha-desktop kernel: [    6.577159] usb 1-1.1: new full speed USB device using uhci_hcd and address 8
Mar 17 17:46:17 maha-desktop kernel: [    6.715335] usb 1-1.1: configuration #1 chosen from 1 choice
Mar 17 17:46:17 maha-desktop kernel: [   10.761542] udevd version 124 started
Mar 17 17:46:17 maha-desktop kernel: [   11.559461] Linux agpgart interface v0.103
Mar 17 17:46:17 maha-desktop kernel: [   11.624244] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 17 17:46:17 maha-desktop kernel: [   11.629631] agpgart: Detected VIA P4M900 chipset
Mar 17 17:46:17 maha-desktop kernel: [   11.637882] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Mar 17 17:46:17 maha-desktop kernel: [   11.733189] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 17 17:46:17 maha-desktop kernel: [   11.976422] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 17 17:46:17 maha-desktop kernel: [   12.008049] ACPI: Power Button (FF) [PWRF]
Mar 17 17:46:17 maha-desktop kernel: [   12.008235] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Mar 17 17:46:17 maha-desktop kernel: [   12.040039] ACPI: Power Button (CM) [PWRB]
Mar 17 17:46:17 maha-desktop kernel: [   12.040213] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Mar 17 17:46:17 maha-desktop kernel: [   12.072036] ACPI: Sleep Button (CM) [SLPB]
Mar 17 17:46:17 maha-desktop kernel: [   12.728045] nvidia: module license 'NVIDIA' taints kernel.
Mar 17 17:46:17 maha-desktop kernel: [   13.229844] parport_pc 00:0c: reported by Plug and Play ACPI
Mar 17 17:46:17 maha-desktop kernel: [   13.229895] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 17 17:46:17 maha-desktop kernel: [   13.465960] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Mar 17 17:46:17 maha-desktop kernel: [   13.465974] nvidia 0000:02:00.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [   13.466232] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
Mar 17 17:46:17 maha-desktop kernel: [   14.408193] Bluetooth: Core ver 2.13
Mar 17 17:46:17 maha-desktop kernel: [   14.464866] NET: Registered protocol family 31
Mar 17 17:46:17 maha-desktop kernel: [   14.464874] Bluetooth: HCI device and connection manager initialized
Mar 17 17:46:17 maha-desktop kernel: [   14.464884] Bluetooth: HCI socket layer initialized
Mar 17 17:46:17 maha-desktop kernel: [   14.488158] Bluetooth: Generic Bluetooth USB driver ver 0.3
Mar 17 17:46:17 maha-desktop kernel: [   14.488333] usbcore: registered new interface driver btusb
Mar 17 17:46:17 maha-desktop kernel: [   14.673586] input: PC Speaker as /devices/platform/pcspkr/input/input5
Mar 17 17:46:17 maha-desktop kernel: [   14.791502] device-mapper: multipath: version 1.0.5 loaded
Mar 17 17:46:17 maha-desktop kernel: [   14.888532] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Mar 17 17:46:17 maha-desktop kernel: [   15.188330] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
Mar 17 17:46:17 maha-desktop kernel: [   15.188818] ndiswrapper 0000:04:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 17 17:46:17 maha-desktop kernel: [   15.646263] ndiswrapper: using IRQ 17
Mar 17 17:46:17 maha-desktop kernel: [   15.825542] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Mar 17 17:46:17 maha-desktop kernel: [   16.057349] wlan0: ethernet device 00:19:5b:53:bd:95 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
Mar 17 17:46:17 maha-desktop kernel: [   16.124218] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Mar 17 17:46:17 maha-desktop kernel: [   16.174128] usbcore: registered new interface driver ndiswrapper
Mar 17 17:46:17 maha-desktop kernel: [   16.627140] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 17 17:46:17 maha-desktop kernel: [   16.627175] HDA Intel 0000:80:01.0: setting latency timer to 64
Mar 17 17:46:17 maha-desktop kernel: [   16.627186] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
Mar 17 17:46:17 maha-desktop kernel: [   18.661065] lp0: using parport0 (interrupt-driven).
Mar 17 17:46:17 maha-desktop kernel: [   18.895727] Adding 1574360k swap on /dev/sdb3.  Priority:-1 extents:1 across:1574360k
Mar 17 17:46:17 maha-desktop kernel: [   19.484598] EXT3 FS on sdb2, internal journal
Mar 17 17:46:17 maha-desktop kernel: [   21.441035] type=1505 audit(1237326375.931:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4363
Mar 17 17:46:17 maha-desktop kernel: [   21.639447] type=1505 audit(1237326376.127:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4368
Mar 17 17:46:17 maha-desktop kernel: [   21.639677] type=1505 audit(1237326376.127:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4368
Mar 17 17:46:17 maha-desktop kernel: [   21.803019] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 17 17:46:17 maha-desktop kernel: [   22.585484] ACPI: WMI: Mapper loaded
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Successfully dropped root privileges.
Mar 17 17:46:18 maha-desktop kernel: [   23.607056] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: avahi-daemon 0.6.23 starting up.
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Successfully called chroot().
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Successfully dropped remaining capabilities.
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: No service file found in /etc/avahi/services.
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Network interface enumeration completed.
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 17 17:46:18 maha-desktop avahi-daemon[4992]: Server startup complete. Host name is maha-desktop.local. Local service cookie is 669163832.
Mar 17 17:46:18 maha-desktop kernel: [   23.664414] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 17 17:46:18 maha-desktop kernel: [   23.664422] apm: disabled - APM is not SMP safe.
Mar 17 17:46:18 maha-desktop kernel: [   23.796440] ppdev: user-space parallel port driver
Mar 17 17:46:18 maha-desktop kernel: [   23.939009] NET: Registered protocol family 10
Mar 17 17:46:18 maha-desktop kernel: [   23.940981] lo: Disabled Privacy Extensions
Mar 17 17:46:20 maha-desktop kernel: [   25.720841] Bridge firewalling registered
Mar 17 17:46:20 maha-desktop avahi-daemon[4992]: Joining mDNS multicast group on interface vnet0.IPv4 with address 192.168.122.1.
Mar 17 17:46:20 maha-desktop avahi-daemon[4992]: New relevant interface vnet0.IPv4 for mDNS.
Mar 17 17:46:20 maha-desktop avahi-daemon[4992]: Registering new address record for 192.168.122.1 on vnet0.IPv4.
Mar 17 17:46:20 maha-desktop kernel: [   25.754283] vnet0: starting userspace STP failed, starting kernel STP
Mar 17 17:46:20 maha-desktop kernel: [   26.289887] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 17 17:46:20 maha-desktop kernel: [   26.290239] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
Mar 17 17:46:20 maha-desktop kernel: [   26.290246] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Mar 17 17:46:20 maha-desktop kernel: [   26.290251] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: started, version 2.45 cachesize 150
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: compile time options: IPv6 GNU-getopt no-ISC-leasefile DBus I18N TFTP
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: reading /etc/resolv.conf
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: using nameserver 192.168.0.1#53
Mar 17 17:46:22 maha-desktop dnsmasq[5479]: read /etc/hosts - 8 addresses
Mar 17 17:46:22 maha-desktop avahi-daemon[4992]: Registering new address record for fe80::e48d:4dff:fe2a:48b9 on vnet0.*.
Mar 17 17:46:22 maha-desktop kernel: [   28.490678] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Mar 17 17:46:22 maha-desktop kernel: [   28.490689] vboxdrv: Successfully done.
Mar 17 17:46:22 maha-desktop kernel: [   28.490693] vboxdrv: Found 2 processor cores.
Mar 17 17:46:22 maha-desktop kernel: [   28.490933] vboxdrv: fAsync=0 offMin=0x636 offMax=0x27b2
Mar 17 17:46:22 maha-desktop kernel: [   28.491022] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Mar 17 17:46:22 maha-desktop kernel: [   28.491028] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
Mar 17 17:46:24 maha-desktop kernel: [   30.349710] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 17 17:46:24 maha-desktop xinetd[5593]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Mar 17 17:46:24 maha-desktop xinetd[5593]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Mar 17 17:46:24 maha-desktop xinetd[5593]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Mar 17 17:46:24 maha-desktop xinetd[5593]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Mar 17 17:46:24 maha-desktop xinetd[5593]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing chargen
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing chargen
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing daytime
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing daytime
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing discard
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing discard
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing echo
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing echo
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing time
Mar 17 17:46:24 maha-desktop xinetd[5593]: removing time
Mar 17 17:46:24 maha-desktop xinetd[5593]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Mar 17 17:46:24 maha-desktop xinetd[5593]: Started working: 0 available services
Mar 17 17:46:25 maha-desktop acpid: client connected from 5702[111:122] 
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Bluetooth daemon
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Starting SDP server
Mar 17 17:46:26 maha-desktop kernel: [   31.683859] Bluetooth: L2CAP ver 2.11
Mar 17 17:46:26 maha-desktop kernel: [   31.683867] Bluetooth: L2CAP socket layer initialized
Mar 17 17:46:26 maha-desktop kernel: [   31.706009] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 17 17:46:26 maha-desktop kernel: [   31.706017] Bluetooth: BNEP filters: protocol multicast
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: bridge pan0 created
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Starting experimental netlink support
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Failed to find Bluetooth netlink family
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 17 17:46:26 maha-desktop kernel: [   31.724062] Bluetooth: SCO (Voice Link) ver 0.6
Mar 17 17:46:26 maha-desktop kernel: [   31.724073] Bluetooth: SCO socket layer initialized
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: HCI dev 0 registered
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: HCI dev 0 up
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Registered interface org.bluez.NetworkPeer on path /org/bluez/hci0
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Registered interface org.bluez.NetworkHub on path /org/bluez/hci0
Mar 17 17:46:26 maha-desktop kernel: [   31.852442] Bluetooth: RFCOMM socket layer initialized
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Registered interface org.bluez.NetworkRouter on path /org/bluez/hci0
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Registered interface org.bluez.Service on path /org/bluez/hci0
Mar 17 17:46:26 maha-desktop kernel: [   31.852472] Bluetooth: RFCOMM TTY layer initialized
Mar 17 17:46:26 maha-desktop kernel: [   31.852477] Bluetooth: RFCOMM ver 1.10
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/hci0
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Adapter /org/bluez/hci0 has been enabled
Mar 17 17:46:26 maha-desktop bluetoothd[5755]: Starting security manager 0
Mar 17 17:46:27 maha-desktop acpid: client connected from 5823[0:0] 
Mar 17 17:46:28 maha-desktop kernel: [   33.563784] eth0: link down
Mar 17 17:46:28 maha-desktop kernel: [   33.564503] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 17 17:46:29 maha-desktop anacron[5860]: Anacron 2.3 started on 2009-03-17
Mar 17 17:46:29 maha-desktop anacron[5860]: Normal exit (0 jobs run)
Mar 17 17:46:29 maha-desktop /usr/sbin/cron[5906]: (CRON) INFO (pidfile fd = 3)
Mar 17 17:46:29 maha-desktop /usr/sbin/cron[5907]: (CRON) STARTUP (fork ok)
Mar 17 17:46:29 maha-desktop /usr/sbin/cron[5907]: (CRON) INFO (Running @reboot jobs)
Mar 17 17:46:29 maha-desktop acpid: client connected from 5823[0:0] 
Mar 17 17:46:30 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:46:30 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:46:30 maha-desktop dhclient: All rights reserved.
Mar 17 17:46:30 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:46:30 maha-desktop dhclient: 
Mar 17 17:46:30 maha-desktop kernel: [   35.939716] NET: Registered protocol family 17
Mar 17 17:46:30 maha-desktop dhclient: Bind socket to interface: No such device
Mar 17 17:46:30 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:46:30 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:46:30 maha-desktop dhclient: All rights reserved.
Mar 17 17:46:30 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:46:30 maha-desktop dhclient: 
Mar 17 17:46:30 maha-desktop dhclient: Bind socket to interface: No such device
Mar 17 17:46:30 maha-desktop kernel: [   36.034829] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 17 17:46:31 maha-desktop kernel: [   36.608013] vnet0: no IPv6 routers present
Mar 17 17:46:31 maha-desktop kernel: [   36.725592] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 17 17:46:32 maha-desktop avahi-daemon[4992]: Registering new address record for fe80::219:5bff:fe53:bd95 on wlan0.*.
Mar 17 17:46:34 maha-desktop pulseaudio[6226]: ltdl-bind-now.c: Failed to find original dlopen loader.

```

---

### Post by mahasmb on 2009-03-18
Second half of syslog file:

```

Mar 17 17:46:34 maha-desktop pulseaudio[6228]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 17 17:46:34 maha-desktop pulseaudio[6228]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 17 17:46:34 maha-desktop kernel: [   39.790812] hda-intel: Invalid position buffer, using LPIB read method instead.
Mar 17 17:46:34 maha-desktop kernel: [   39.790841] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Mar 17 17:46:35 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:46:35 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:46:35 maha-desktop dhclient: All rights reserved.
Mar 17 17:46:35 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:46:35 maha-desktop dhclient: 
Mar 17 17:46:37 maha-desktop dhclient: Listening on LPF/wlan0/00:19:5b:53:bd:95
Mar 17 17:46:37 maha-desktop dhclient: Sending on   LPF/wlan0/00:19:5b:53:bd:95
Mar 17 17:46:37 maha-desktop dhclient: Sending on   Socket/fallback
Mar 17 17:46:37 maha-desktop dhclient: DHCPREQUEST of 192.168.0.182 on wlan0 to 255.255.255.255 port 67
Mar 17 17:46:39 maha-desktop x-session-manager[6163]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup. 
Mar 17 17:46:39 maha-desktop x-session-manager[6163]: atk-bridge-WARNING: IOR not set. 
Mar 17 17:46:39 maha-desktop x-session-manager[6163]: atk-bridge-WARNING: Could not locate registry 
Mar 17 17:46:40 maha-desktop dhclient: DHCPREQUEST of 192.168.0.182 on wlan0 to 255.255.255.255 port 67
Mar 17 17:46:41 maha-desktop kernel: [   47.160013] wlan0: no IPv6 routers present
Mar 17 17:46:47 maha-desktop dhclient: DHCPREQUEST of 192.168.0.182 on wlan0 to 255.255.255.255 port 67
Mar 17 17:46:47 maha-desktop dhclient: DHCPNAK from 192.168.0.1
Mar 17 17:46:47 maha-desktop avahi-autoipd(wlan0)[6364]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Mar 17 17:46:47 maha-desktop avahi-autoipd(wlan0)[6364]: Successfully called chroot().
Mar 17 17:46:47 maha-desktop avahi-autoipd(wlan0)[6364]: Successfully dropped root privileges.
Mar 17 17:46:47 maha-desktop avahi-autoipd(wlan0)[6364]: Starting with address 169.254.7.166
Mar 17 17:46:49 maha-desktop x-session-manager[6163]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Mar 17 17:46:52 maha-desktop avahi-autoipd(wlan0)[6364]: Callout BIND, address 169.254.7.166 on interface wlan0
Mar 17 17:46:52 maha-desktop avahi-daemon[4992]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.166.
Mar 17 17:46:52 maha-desktop avahi-daemon[4992]: New relevant interface wlan0.IPv4 for mDNS.
Mar 17 17:46:52 maha-desktop avahi-daemon[4992]: Registering new address record for 169.254.7.166 on wlan0.IPv4.
Mar 17 17:46:56 maha-desktop avahi-autoipd(wlan0)[6364]: Successfully claimed IP address 169.254.7.166
Mar 17 17:46:56 maha-desktop avahi-autoipd(wlan0)[6364]: Got SIGTERM, quitting.
Mar 17 17:46:56 maha-desktop avahi-autoipd(wlan0)[6364]: Callout STOP, address 169.254.7.166 on interface wlan0
Mar 17 17:46:56 maha-desktop avahi-daemon[4992]: Withdrawing address record for 169.254.7.166 on wlan0.
Mar 17 17:46:56 maha-desktop avahi-daemon[4992]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.166.
Mar 17 17:46:56 maha-desktop avahi-daemon[4992]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 17 17:46:56 maha-desktop avahi-autoipd(wlan0)[6365]: client: RTNETLINK answers: No such process
Mar 17 17:46:57 maha-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Mar 17 17:46:57 maha-desktop dhclient: DHCPOFFER of 192.168.0.158 from 192.168.0.1
Mar 17 17:46:57 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 17 17:46:57 maha-desktop dhclient: DHCPACK of 192.168.0.158 from 192.168.0.1
Mar 17 17:46:57 maha-desktop avahi-daemon[4992]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.158.
Mar 17 17:46:57 maha-desktop avahi-daemon[4992]: New relevant interface wlan0.IPv4 for mDNS.
Mar 17 17:46:57 maha-desktop avahi-daemon[4992]: Registering new address record for 192.168.0.158 on wlan0.IPv4.
Mar 17 17:46:57 maha-desktop dhclient: bound to 192.168.0.158 -- renewal in 40417 seconds.
Mar 17 17:46:59 maha-desktop x-session-manager[6163]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 17 17:46:59 maha-desktop x-session-manager[6163]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory) 
Mar 17 17:47:00 maha-desktop pulseaudio[6228]: module-x11-xsmp.c: X11 session manager not running.
Mar 17 17:47:00 maha-desktop pulseaudio[6228]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 17 17:48:04 maha-desktop kernel: [  130.386597] ppdev0: registered pardevice
Mar 17 17:48:04 maha-desktop kernel: [  130.432028] ppdev0: unregistered pardevice
Mar 17 17:48:06 maha-desktop kernel: [  131.768579] ppdev0: registered pardevice
Mar 17 17:48:06 maha-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 17 17:48:06 maha-desktop kernel: [  131.816325] ppdev0: unregistered pardevice
Mar 17 17:48:07 maha-desktop kernel: [  133.278540] ppdev0: registered pardevice
Mar 17 17:48:07 maha-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 17 17:48:07 maha-desktop kernel: [  133.324273] ppdev0: unregistered pardevice
Mar 17 17:48:52 maha-desktop kernel: [  177.705627] device wlan0 entered promiscuous mode
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: HCI dev 0 down
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Unregistered interface org.bluez.NetworkPeer on path /org/bluez/hci0
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Unregistered interface org.bluez.NetworkHub on path /org/bluez/hci0
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Unregistered interface org.bluez.NetworkRouter on path /org/bluez/hci0
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Adapter /org/bluez/hci0 has been disabled
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Stopping security manager 0
Mar 17 17:48:52 maha-desktop kernel: [  177.738277] btusb_intr_complete: hci0 urb f4038a00 failed to resubmit (2)
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: HCI dev 0 unregistered
Mar 17 17:48:52 maha-desktop bluetoothd[5755]: Unregister path: /org/bluez/hci0
Mar 17 17:50:01 maha-desktop /USR/SBIN/CRON[6844]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 17:50:01 maha-desktop dnsmasq[5479]: reading /etc/resolv.conf
Mar 17 17:50:01 maha-desktop dnsmasq[5479]: using nameserver 192.168.0.1#53
Mar 17 17:54:44 maha-desktop kernel: [  530.287712] Too big adjustment 32
Mar 17 17:55:01 maha-desktop /USR/SBIN/CRON[7471]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 17:57:33 maha-desktop kernel: [  698.563187] device wlan0 left promiscuous mode
Mar 17 17:57:33 maha-desktop avahi-daemon[4992]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 17 17:57:33 maha-desktop avahi-daemon[4992]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.158.
Mar 17 17:57:33 maha-desktop dhclient: receive_packet failed on wlan0: Network is down
Mar 17 17:57:33 maha-desktop avahi-daemon[4992]: Withdrawing address record for fe80::219:5bff:fe53:bd95 on wlan0.
Mar 17 17:57:33 maha-desktop avahi-daemon[4992]: Withdrawing address record for 192.168.0.158 on wlan0.
Mar 17 17:57:33 maha-desktop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6441
Mar 17 17:57:33 maha-desktop dhclient: killed old client process, removed PID file
Mar 17 17:57:33 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:57:33 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:57:33 maha-desktop dhclient: All rights reserved.
Mar 17 17:57:33 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:57:33 maha-desktop dhclient: 
Mar 17 17:57:33 maha-desktop dhclient: Bind socket to interface: No such device
Mar 17 17:57:33 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:57:33 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:57:33 maha-desktop dhclient: All rights reserved.
Mar 17 17:57:33 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:57:33 maha-desktop dhclient: 
Mar 17 17:57:33 maha-desktop dhclient: Bind socket to interface: No such device
Mar 17 17:57:33 maha-desktop kernel: [  698.774319] device wlan0 entered promiscuous mode
Mar 17 17:57:33 maha-desktop kernel: [  699.035852] device wlan0 left promiscuous mode
Mar 17 17:57:33 maha-desktop kernel: [  699.082111] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 17 17:57:33 maha-desktop kernel: [  699.082128] device wlan0 entered promiscuous mode
Mar 17 17:57:34 maha-desktop kernel: [  700.424991] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 17 17:57:36 maha-desktop avahi-daemon[4992]: Registering new address record for fe80::219:5bff:fe53:bd95 on wlan0.*.
Mar 17 17:57:41 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 17 17:57:41 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 17 17:57:41 maha-desktop dhclient: All rights reserved.
Mar 17 17:57:41 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 17 17:57:41 maha-desktop dhclient: 
Mar 17 17:57:42 maha-desktop dhclient: Listening on LPF/wlan0/00:19:5b:53:bd:95
Mar 17 17:57:42 maha-desktop dhclient: Sending on   LPF/wlan0/00:19:5b:53:bd:95
Mar 17 17:57:42 maha-desktop dhclient: Sending on   Socket/fallback
Mar 17 17:57:42 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 17 17:57:45 maha-desktop kernel: [  710.560513] wlan0: no IPv6 routers present
Mar 17 17:57:49 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 17 17:57:49 maha-desktop dhclient: DHCPACK of 192.168.0.158 from 192.168.0.1
Mar 17 17:57:49 maha-desktop avahi-daemon[4992]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.158.
Mar 17 17:57:49 maha-desktop avahi-daemon[4992]: New relevant interface wlan0.IPv4 for mDNS.
Mar 17 17:57:49 maha-desktop avahi-daemon[4992]: Registering new address record for 192.168.0.158 on wlan0.IPv4.
Mar 17 17:57:49 maha-desktop dhclient: bound to 192.168.0.158 -- renewal in 41230 seconds.
Mar 17 18:00:01 maha-desktop /USR/SBIN/CRON[7849]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:05:01 maha-desktop /USR/SBIN/CRON[8114]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:09:33 maha-desktop kernel: [ 1418.760544] usb 3-2: new full speed USB device using uhci_hcd and address 2
Mar 17 18:09:33 maha-desktop kernel: [ 1418.931235] usb 3-2: configuration #1 chosen from 1 choice
Mar 17 18:09:36 maha-desktop kernel: [ 1422.200659] usb 3-2: USB disconnect, address 2
Mar 17 18:09:37 maha-desktop kernel: [ 1422.936548] usb 3-2: new full speed USB device using uhci_hcd and address 3
Mar 17 18:09:37 maha-desktop kernel: [ 1423.105683] usb 3-2: configuration #1 chosen from 1 choice
Mar 17 18:10:01 maha-desktop /USR/SBIN/CRON[8460]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:15:01 maha-desktop /USR/SBIN/CRON[8720]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:17:01 maha-desktop /USR/SBIN/CRON[8847]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 18:19:07 maha-desktop kernel: [ 1993.344838] usb 3-2: USB disconnect, address 3
Mar 17 18:19:08 maha-desktop kernel: [ 1993.836171] usb 3-2: new full speed USB device using uhci_hcd and address 4
Mar 17 18:19:08 maha-desktop kernel: [ 1994.006434] usb 3-2: configuration #1 chosen from 1 choice
Mar 17 18:20:01 maha-desktop /USR/SBIN/CRON[9040]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:23:49 maha-desktop dnsmasq[5479]: reading /etc/resolv.conf
Mar 17 18:23:49 maha-desktop dnsmasq[5479]: using nameserver 192.168.0.1#53
Mar 17 18:25:01 maha-desktop /USR/SBIN/CRON[9328]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:30:02 maha-desktop /USR/SBIN/CRON[9603]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:35:01 maha-desktop /USR/SBIN/CRON[9881]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:39:01 maha-desktop kernel: [ 3186.968673] usb 3-2: USB disconnect, address 4
Mar 17 18:40:01 maha-desktop /USR/SBIN/CRON[10149]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:45:01 maha-desktop /USR/SBIN/CRON[10392]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:50:01 maha-desktop /USR/SBIN/CRON[10653]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 18:55:02 maha-desktop /USR/SBIN/CRON[10913]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:00:01 maha-desktop /USR/SBIN/CRON[11184]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:05:01 maha-desktop /USR/SBIN/CRON[11449]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:10:01 maha-desktop /USR/SBIN/CRON[11706]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:15:01 maha-desktop /USR/SBIN/CRON[11944]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:17:01 maha-desktop /USR/SBIN/CRON[12067]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 19:20:01 maha-desktop /USR/SBIN/CRON[12237]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:25:01 maha-desktop /USR/SBIN/CRON[12538]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:30:01 maha-desktop /USR/SBIN/CRON[12830]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:35:01 maha-desktop /USR/SBIN/CRON[13097]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:40:01 maha-desktop /USR/SBIN/CRON[13405]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:45:01 maha-desktop /USR/SBIN/CRON[13684]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:50:01 maha-desktop /USR/SBIN/CRON[13949]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 19:55:01 maha-desktop /USR/SBIN/CRON[14210]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:00:01 maha-desktop /USR/SBIN/CRON[14502]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:05:01 maha-desktop /USR/SBIN/CRON[14787]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:10:01 maha-desktop /USR/SBIN/CRON[15059]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:15:01 maha-desktop /USR/SBIN/CRON[15339]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:17:01 maha-desktop /USR/SBIN/CRON[15464]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 20:20:01 maha-desktop /USR/SBIN/CRON[15634]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:25:01 maha-desktop /USR/SBIN/CRON[15874]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:30:01 maha-desktop /USR/SBIN/CRON[16147]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:35:01 maha-desktop /USR/SBIN/CRON[16411]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:40:01 maha-desktop /USR/SBIN/CRON[16670]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:45:01 maha-desktop /USR/SBIN/CRON[16918]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:50:01 maha-desktop /USR/SBIN/CRON[17158]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 20:55:01 maha-desktop /USR/SBIN/CRON[17416]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:00:01 maha-desktop /USR/SBIN/CRON[17688]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:05:01 maha-desktop /USR/SBIN/CRON[17949]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:10:01 maha-desktop /USR/SBIN/CRON[18210]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:15:01 maha-desktop /USR/SBIN/CRON[18470]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:17:01 maha-desktop /USR/SBIN/CRON[18592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 21:20:01 maha-desktop /USR/SBIN/CRON[18762]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:25:01 maha-desktop /USR/SBIN/CRON[19023]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:30:02 maha-desktop /USR/SBIN/CRON[19298]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:35:01 maha-desktop /USR/SBIN/CRON[19558]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:40:01 maha-desktop /USR/SBIN/CRON[19816]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:45:01 maha-desktop /USR/SBIN/CRON[20075]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:50:01 maha-desktop /USR/SBIN/CRON[20317]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 21:55:01 maha-desktop /USR/SBIN/CRON[20577]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:00:01 maha-desktop /USR/SBIN/CRON[20848]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:05:01 maha-desktop /USR/SBIN/CRON[21090]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:10:01 maha-desktop /USR/SBIN/CRON[21332]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:15:01 maha-desktop /USR/SBIN/CRON[21571]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:17:01 maha-desktop /USR/SBIN/CRON[21694]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 22:20:01 maha-desktop /USR/SBIN/CRON[21863]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:25:01 maha-desktop /USR/SBIN/CRON[22105]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:30:01 maha-desktop /USR/SBIN/CRON[22395]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:35:01 maha-desktop /USR/SBIN/CRON[22712]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:40:01 maha-desktop /USR/SBIN/CRON[23021]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:45:01 maha-desktop /USR/SBIN/CRON[23327]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:45:13 maha-desktop kernel: [17958.823944] device wlan0 left promiscuous mode
Mar 17 22:50:01 maha-desktop /USR/SBIN/CRON[23623]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 22:55:02 maha-desktop /USR/SBIN/CRON[23986]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:00:02 maha-desktop /USR/SBIN/CRON[24301]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:05:01 maha-desktop /USR/SBIN/CRON[24546]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:10:01 maha-desktop /USR/SBIN/CRON[24788]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:15:01 maha-desktop /USR/SBIN/CRON[25047]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:17:01 maha-desktop /USR/SBIN/CRON[25189]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 23:20:01 maha-desktop /USR/SBIN/CRON[25358]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:25:01 maha-desktop /USR/SBIN/CRON[25620]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:30:01 maha-desktop /USR/SBIN/CRON[25900]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:35:01 maha-desktop /USR/SBIN/CRON[26159]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:40:01 maha-desktop /USR/SBIN/CRON[26419]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:45:01 maha-desktop /USR/SBIN/CRON[26678]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:50:01 maha-desktop /USR/SBIN/CRON[26940]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 17 23:55:01 maha-desktop /USR/SBIN/CRON[27370]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:00:01 maha-desktop /USR/SBIN/CRON[27675]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:05:01 maha-desktop /USR/SBIN/CRON[27926]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:10:01 maha-desktop /USR/SBIN/CRON[28220]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:15:01 maha-desktop /USR/SBIN/CRON[28479]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:17:01 maha-desktop /USR/SBIN/CRON[28602]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 00:20:01 maha-desktop /USR/SBIN/CRON[28771]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:25:01 maha-desktop /USR/SBIN/CRON[29030]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:30:01 maha-desktop /USR/SBIN/CRON[29302]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:35:01 maha-desktop /USR/SBIN/CRON[29560]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:40:01 maha-desktop /USR/SBIN/CRON[29819]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:45:01 maha-desktop /USR/SBIN/CRON[30079]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:50:01 maha-desktop /USR/SBIN/CRON[30346]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 00:55:01 maha-desktop /USR/SBIN/CRON[30605]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:00:01 maha-desktop /USR/SBIN/CRON[30876]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:05:01 maha-desktop /USR/SBIN/CRON[31134]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:10:01 maha-desktop /USR/SBIN/CRON[31396]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:15:01 maha-desktop /USR/SBIN/CRON[31654]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:17:01 maha-desktop /USR/SBIN/CRON[31778]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 01:20:01 maha-desktop /USR/SBIN/CRON[31951]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:25:01 maha-desktop /USR/SBIN/CRON[32208]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:30:02 maha-desktop /USR/SBIN/CRON[32481]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:35:01 maha-desktop /USR/SBIN/CRON[32739]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:40:01 maha-desktop /USR/SBIN/CRON[530]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:45:01 maha-desktop /USR/SBIN/CRON[788]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:50:01 maha-desktop /USR/SBIN/CRON[1051]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 01:55:01 maha-desktop /USR/SBIN/CRON[1321]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:00:01 maha-desktop /USR/SBIN/CRON[1611]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:05:01 maha-desktop /USR/SBIN/CRON[1858]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:10:01 maha-desktop /USR/SBIN/CRON[2141]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:15:01 maha-desktop /USR/SBIN/CRON[2410]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:17:01 maha-desktop /USR/SBIN/CRON[2582]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 02:20:01 maha-desktop /USR/SBIN/CRON[2764]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:25:01 maha-desktop /USR/SBIN/CRON[3043]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:30:01 maha-desktop /USR/SBIN/CRON[3315]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:35:01 maha-desktop /USR/SBIN/CRON[3591]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:40:01 maha-desktop /USR/SBIN/CRON[3854]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:45:01 maha-desktop /USR/SBIN/CRON[4145]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:50:01 maha-desktop /USR/SBIN/CRON[4443]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 02:55:01 maha-desktop /USR/SBIN/CRON[4709]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:00:01 maha-desktop /USR/SBIN/CRON[4987]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:05:01 maha-desktop /USR/SBIN/CRON[5252]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:10:01 maha-desktop /USR/SBIN/CRON[5521]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:15:01 maha-desktop /USR/SBIN/CRON[5860]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:17:01 maha-desktop /USR/SBIN/CRON[5988]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 03:20:01 maha-desktop /USR/SBIN/CRON[6165]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:25:01 maha-desktop /USR/SBIN/CRON[6468]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:30:02 maha-desktop /USR/SBIN/CRON[6751]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:35:01 maha-desktop /USR/SBIN/CRON[7099]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:40:01 maha-desktop /USR/SBIN/CRON[7421]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:45:01 maha-desktop /USR/SBIN/CRON[7695]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:50:01 maha-desktop /USR/SBIN/CRON[7942]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 03:55:01 maha-desktop /USR/SBIN/CRON[8186]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:00:01 maha-desktop /USR/SBIN/CRON[8476]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:05:01 maha-desktop /USR/SBIN/CRON[8742]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:10:01 maha-desktop /USR/SBIN/CRON[8848]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:15:01 maha-desktop /USR/SBIN/CRON[8898]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:17:01 maha-desktop /USR/SBIN/CRON[8940]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 04:20:01 maha-desktop /USR/SBIN/CRON[8987]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:25:01 maha-desktop /USR/SBIN/CRON[9040]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:30:01 maha-desktop /USR/SBIN/CRON[9094]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:35:01 maha-desktop /USR/SBIN/CRON[9147]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:40:01 maha-desktop /USR/SBIN/CRON[9209]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:45:01 maha-desktop /USR/SBIN/CRON[9261]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:50:01 maha-desktop /USR/SBIN/CRON[9314]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 04:58:57 maha-desktop syslogd 1.5.0#2ubuntu6: restart.
Mar 18 04:58:57 maha-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar 18 04:58:57 maha-desktop kernel: Cannot find map file.
Mar 18 04:58:57 maha-desktop kernel: Loaded 67655 symbols from 88 modules.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] DMI 2.4 present.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] RAMDISK: 377a2000 - 37fefd91
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0014 (r0 P4M900)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: RSDT 7FEE3000, 0034 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: FACP 7FEE3080, 0074 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3100, 62D0 (r1 P4M900 AWRDACPI     1000 MSFT  3000000)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: HPET 7FEE94C0, 0038 (r1 P4M900 AWRDACPI 42302E31 AWRD       98)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: MCFG 7FEE9500, 003C (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: APIC 7FEE9400, 0090 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] 896MB LOWMEM available.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   low ram: 00000000 - 38000000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   bootmap 00011000 - 00018000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #4 [00377a2000 - 0037fefd91]          RAMDISK ==> [00377a2000 - 0037fefd91]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] found SMP MP-table at [c00f3d60] 000f3d60
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Zone PFN ranges:
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007fee0
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Movable zone start PFN for each node
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] On node 0 totalpages: 523887
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Mar 18 04:58:57 maha-desktop kernel: [    0.000000]   HighMem zone: 292034 pages, LIFO batch:31
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 5, version 3, address 0xfecc0000, GSI 24-47
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519281
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Kernel command line: root=UUID=fab527b5-514d-4898-9584-cd6a6f071a5c ro quiet splash 
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Initializing CPU#0
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] TSC: using PIT calibration value
Mar 18 04:58:57 maha-desktop kernel: [    0.000000] Detected 2999.923 MHz processor.
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] console [tty0] enabled
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Memory: 2061984k/2096000k available (2576k kernel code, 32852k reserved, 1165k data, 424k init, 1178496k highmem)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] virtual kernel memory layout:
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] hpet clockevent registered
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.84 BogoMIPS (lpj=11999692)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Security Framework initialized
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] using mwait in idle threads.
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Mar 18 04:58:57 maha-desktop kernel: [    0.018664] ACPI: Core revision 20080609
Mar 18 04:58:57 maha-desktop kernel: [    0.022419] ACPI: Checking initramfs for custom DSDT
Mar 18 04:58:57 maha-desktop kernel: [    0.372417] ENABLING IO-APIC IRQs
Mar 18 04:58:57 maha-desktop kernel: [    0.372608] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 18 04:58:57 maha-desktop kernel: [    0.414544] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Mar 18 04:58:57 maha-desktop kernel: [    0.416026] Booting processor 1/1 ip 6000
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Initializing CPU#1
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5999.85 BogoMIPS (lpj=11999708)
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Mar 18 04:58:57 maha-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 04:58:57 maha-desktop kernel: [    0.500434] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Mar 18 04:58:57 maha-desktop kernel: [    0.500463] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 18 04:58:57 maha-desktop kernel: [    0.504061] Brought up 2 CPUs
Mar 18 04:58:57 maha-desktop kernel: [    0.504067] Total of 2 processors activated (11999.70 BogoMIPS).
Mar 18 04:58:57 maha-desktop kernel: [    0.504092] CPU0 attaching sched-domain:
Mar 18 04:58:57 maha-desktop kernel: [    0.504096]  domain 0: span 0-1 level SIBLING
Mar 18 04:58:57 maha-desktop kernel: [    0.504100]   groups: 0 1
Mar 18 04:58:57 maha-desktop kernel: [    0.504109] CPU1 attaching sched-domain:
Mar 18 04:58:57 maha-desktop kernel: [    0.504112]  domain 0: span 0-1 level SIBLING
Mar 18 04:58:57 maha-desktop kernel: [    0.504116]   groups: 1 0
Mar 18 04:58:57 maha-desktop kernel: [    0.504216] net_namespace: 840 bytes
Mar 18 04:58:57 maha-desktop kernel: [    0.504216] Booting paravirtualized kernel on bare hardware
Mar 18 04:58:57 maha-desktop kernel: [    0.504434] Time:  4:58:33  Date: 03/18/09
Mar 18 04:58:57 maha-desktop kernel: [    0.504473] NET: Registered protocol family 16
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] EISA bus registered
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] ACPI: bus type pci registered
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] PCI: MCFG area at e0000000 reserved in E820
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] PCI: Using MMCONFIG for extended config space
Mar 18 04:58:57 maha-desktop kernel: [    0.504507] PCI: Using configuration type 1 for base access
Mar 18 04:58:57 maha-desktop kernel: [    0.509464] ACPI: EC: Look up EC in DSDT
Mar 18 04:58:57 maha-desktop kernel: [    0.526720] ACPI: Interpreter enabled
Mar 18 04:58:57 maha-desktop kernel: [    0.526726] ACPI: (supports S0 S1 S4 S5)
Mar 18 04:58:57 maha-desktop kernel: [    0.526751] ACPI: Using IOAPIC for interrupt routing
Mar 18 04:58:57 maha-desktop kernel: [    0.540595] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 18 04:58:57 maha-desktop kernel: [    0.540595] PCI: 0000:00:00.0 reg 10 32bit mmio: [d8000000, dfffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.540672] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.540679] pci 0000:00:02.0: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.540751] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.540757] pci 0000:00:03.0: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.540820] PCI: 0000:00:0f.0 reg 10 io port: [fc00, fc07]
Mar 18 04:58:57 maha-desktop kernel: [    0.540829] PCI: 0000:00:0f.0 reg 14 io port: [f800, f803]
Mar 18 04:58:57 maha-desktop kernel: [    0.540838] PCI: 0000:00:0f.0 reg 18 io port: [f400, f407]
Mar 18 04:58:57 maha-desktop kernel: [    0.540847] PCI: 0000:00:0f.0 reg 1c io port: [f000, f003]
Mar 18 04:58:57 maha-desktop kernel: [    0.540856] PCI: 0000:00:0f.0 reg 20 io port: [ec00, ec0f]
Mar 18 04:58:57 maha-desktop kernel: [    0.540864] PCI: 0000:00:0f.0 reg 24 io port: [e800, e8ff]
Mar 18 04:58:57 maha-desktop kernel: [    0.540944] PCI: 0000:00:0f.1 reg 20 io port: [e400, e40f]
Mar 18 04:58:57 maha-desktop kernel: [    0.541038] PCI: 0000:00:10.0 reg 20 io port: [e000, e01f]
Mar 18 04:58:57 maha-desktop kernel: [    0.541067] pci 0000:00:10.0: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541070] pci 0000:00:10.0: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541073] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541078] pci 0000:00:10.0: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541134] PCI: 0000:00:10.1 reg 20 io port: [dc00, dc1f]
Mar 18 04:58:57 maha-desktop kernel: [    0.541163] pci 0000:00:10.1: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541166] pci 0000:00:10.1: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541168] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541174] pci 0000:00:10.1: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541230] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
Mar 18 04:58:57 maha-desktop kernel: [    0.541259] pci 0000:00:10.2: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541261] pci 0000:00:10.2: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541264] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541269] pci 0000:00:10.2: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541325] PCI: 0000:00:10.3 reg 20 io port: [d400, d41f]
Mar 18 04:58:57 maha-desktop kernel: [    0.541354] pci 0000:00:10.3: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541356] pci 0000:00:10.3: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541359] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541365] pci 0000:00:10.3: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541399] PCI: 0000:00:10.4 reg 10 32bit mmio: [fdfff000, fdfff0ff]
Mar 18 04:58:57 maha-desktop kernel: [    0.541450] pci 0000:00:10.4: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541452] pci 0000:00:10.4: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541455] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541460] pci 0000:00:10.4: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541660] PCI: 0000:00:12.0 reg 10 io port: [d000, d0ff]
Mar 18 04:58:57 maha-desktop kernel: [    0.541669] PCI: 0000:00:12.0 reg 14 32bit mmio: [fdffe000, fdffe0ff]
Mar 18 04:58:57 maha-desktop kernel: [    0.541715] pci 0000:00:12.0: supports D1
Mar 18 04:58:57 maha-desktop kernel: [    0.541718] pci 0000:00:12.0: supports D2
Mar 18 04:58:57 maha-desktop kernel: [    0.541720] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.541726] pci 0000:00:12.0: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.541940] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
Mar 18 04:58:57 maha-desktop kernel: [    0.541946] PCI: bridge 0000:00:01.0 32bit mmio: [fdc00000, fdcfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.541952] PCI: bridge 0000:00:01.0 32bit mmio pref: [fdb00000, fdbfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542000] PCI: 0000:02:00.0 reg 10 32bit mmio: [fa000000, faffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542015] PCI: 0000:02:00.0 reg 14 64bit mmio: [c0000000, cfffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542029] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542038] PCI: 0000:02:00.0 reg 24 io port: [bc00, bc7f]
Mar 18 04:58:57 maha-desktop kernel: [    0.542046] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542119] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542124] PCI: bridge 0000:00:02.0 32bit mmio: [f8000000, fbffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542133] PCI: bridge 0000:00:02.0 64bit mmio pref: [c0000000, cfffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542193] PCI: bridge 0000:00:03.0 io port: [a000, afff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542199] PCI: bridge 0000:00:03.0 32bit mmio: [fde00000, fdefffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542207] PCI: bridge 0000:00:03.0 64bit mmio pref: [fdd00000, fddfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.542264] PCI: 0000:04:04.0 reg 10 32bit mmio: [fdaf0000, fdafffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.544127] pci 0000:00:13.1: transparent bridge
Mar 18 04:58:57 maha-desktop kernel: [    0.544132] PCI: bridge 0000:00:13.1 io port: [9000, 9fff]
Mar 18 04:58:57 maha-desktop kernel: [    0.544138] PCI: bridge 0000:00:13.1 32bit mmio: [fda00000, fdafffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.544146] PCI: bridge 0000:00:13.1 64bit mmio pref: [fd900000, fd9fffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.544173] bus 00 -> node 0
Mar 18 04:58:57 maha-desktop kernel: [    0.544185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 18 04:58:57 maha-desktop kernel: [    0.544811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
Mar 18 04:58:57 maha-desktop kernel: [    0.545025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Mar 18 04:58:57 maha-desktop kernel: [    0.545238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] ACPI: PCI Root Bridge [PCI1] (0000:80)
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] PCI: 0000:80:01.0 reg 10 64bit mmio: [bfffc000, bfffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] pci 0000:80:01.0: PME# disabled
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] bus 80 -> node 0
Mar 18 04:58:57 maha-desktop kernel: [    0.634778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
Mar 18 04:58:57 maha-desktop kernel: [    0.636360] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Mar 18 04:58:57 maha-desktop kernel: [    0.636691] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Mar 18 04:58:57 maha-desktop kernel: [    0.637027] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
Mar 18 04:58:57 maha-desktop kernel: [    0.637358] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
Mar 18 04:58:57 maha-desktop kernel: [    0.637648] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 18 04:58:57 maha-desktop kernel: [    0.637932] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 18 04:58:57 maha-desktop kernel: [    0.638212] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar 18 04:58:57 maha-desktop kernel: [    0.638518] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
Mar 18 04:58:57 maha-desktop kernel: [    0.638634] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 18 04:58:57 maha-desktop kernel: [    0.638634] pnp: PnP ACPI init
Mar 18 04:58:57 maha-desktop kernel: [    0.638634] ACPI: bus type pnp registered
Mar 18 04:58:57 maha-desktop kernel: [    0.648588] pnp: PnP ACPI: found 19 devices
Mar 18 04:58:57 maha-desktop kernel: [    0.648588] ACPI: ACPI bus type pnp unregistered
Mar 18 04:58:57 maha-desktop kernel: [    0.648588] PnPBIOS: Disabled by ACPI PNP
Mar 18 04:58:57 maha-desktop kernel: [    0.648588] PCI: Using ACPI for IRQ routing
Mar 18 04:58:57 maha-desktop kernel: [    0.652051] NET: Registered protocol family 8
Mar 18 04:58:57 maha-desktop kernel: [    0.652055] NET: Registered protocol family 20
Mar 18 04:58:57 maha-desktop kernel: [    0.652081] NetLabel: Initializing
Mar 18 04:58:57 maha-desktop kernel: [    0.652081] NetLabel:  domain hash size = 128
Mar 18 04:58:57 maha-desktop kernel: [    0.652081] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 18 04:58:57 maha-desktop kernel: [    0.652088] NetLabel:  unlabeled traffic allowed by default
Mar 18 04:58:57 maha-desktop kernel: [    0.652097] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
Mar 18 04:58:57 maha-desktop kernel: [    0.652104] hpet0: 3 32-bit timers, 14318180 Hz
Mar 18 04:58:57 maha-desktop kernel: [    0.654504] tracer: 772 pages allocated for 65536 entries of 48 bytes
Mar 18 04:58:57 maha-desktop kernel: [    0.654507]    actual entries 65620
Mar 18 04:58:57 maha-desktop kernel: [    0.654658] AppArmor: AppArmor Filesystem Enabled
Mar 18 04:58:57 maha-desktop kernel: [    0.654682] ACPI: RTC can wake from S4
Mar 18 04:58:57 maha-desktop kernel: [    0.656045] Switched to high resolution mode on CPU 0
Mar 18 04:58:57 maha-desktop kernel: [    0.656490] Switched to high resolution mode on CPU 1
Mar 18 04:58:57 maha-desktop kernel: [    0.656532] system 00:01: ioport range 0x400-0x47f has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656537] system 00:01: ioport range 0x500-0x50f has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656547] system 00:02: iomem range 0xf0001000-0xf0001fff has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656556] system 00:03: iomem range 0xf0002000-0xf0002fff has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656566] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656571] system 00:04: ioport range 0x800-0x805 has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656575] system 00:04: ioport range 0x290-0x297 has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656578] system 00:04: ioport range 0x880-0x88f has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656602] system 00:0f: iomem range 0xf0000000-0xf0000fff has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656613] system 00:10: iomem range 0xe0000000-0xefffffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656623] system 00:12: iomem range 0xf0000-0xfffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656628] system 00:12: iomem range 0xfe800000-0xfe8000ff has been reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656632] system 00:12: iomem range 0x7fee0000-0x7fefffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656636] system 00:12: iomem range 0xffff0000-0xffffffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656640] system 00:12: iomem range 0x0-0x9ffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656644] system 00:12: iomem range 0x100000-0x7fedffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656647] system 00:12: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656651] system 00:12: iomem range 0xfee00000-0xfee00fff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.656655] system 00:12: iomem range 0xfff80000-0xfffeffff could not be reserved
Mar 18 04:58:57 maha-desktop kernel: [    0.692274] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 18 04:58:57 maha-desktop kernel: [    0.692279] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Mar 18 04:58:57 maha-desktop kernel: [    0.692287] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfdcfffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692293] pci 0000:00:01.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692305] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
Mar 18 04:58:57 maha-desktop kernel: [    0.692310] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
Mar 18 04:58:57 maha-desktop kernel: [    0.692317] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692322] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692331] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
Mar 18 04:58:57 maha-desktop kernel: [    0.692335] pci 0000:00:03.0:   IO window: 0xa000-0xafff
Mar 18 04:58:57 maha-desktop kernel: [    0.692343] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692349] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692359] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
Mar 18 04:58:57 maha-desktop kernel: [    0.692363] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
Mar 18 04:58:57 maha-desktop kernel: [    0.692370] pci 0000:00:13.1:   MEM window: 0xfda00000-0xfdafffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692375] pci 0000:00:13.1:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Mar 18 04:58:57 maha-desktop kernel: [    0.692394] pci 0000:00:01.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    0.692411] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
Mar 18 04:58:57 maha-desktop kernel: [    0.692417] pci 0000:00:02.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    0.692430] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
Mar 18 04:58:57 maha-desktop kernel: [    0.692437] pci 0000:00:03.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    0.692447] pci 0000:00:13.1: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    0.692452] bus: 00 index 0 io port: [0, ffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692455] bus: 00 index 1 mmio: [0, ffffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692458] bus: 01 index 0 io port: [c000, cfff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692461] bus: 01 index 1 mmio: [fdc00000, fdcfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692464] bus: 01 index 2 mmio: [fdb00000, fdbfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692466] bus: 01 index 3 mmio: [0, 0]
Mar 18 04:58:57 maha-desktop kernel: [    0.692469] bus: 02 index 0 io port: [b000, bfff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692472] bus: 02 index 1 mmio: [f8000000, fbffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692474] bus: 02 index 2 mmio: [c0000000, cfffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692477] bus: 02 index 3 mmio: [0, 0]
Mar 18 04:58:57 maha-desktop kernel: [    0.692480] bus: 03 index 0 io port: [a000, afff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692483] bus: 03 index 1 mmio: [fde00000, fdefffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692485] bus: 03 index 2 mmio: [fdd00000, fddfffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692488] bus: 03 index 3 mmio: [0, 0]
Mar 18 04:58:57 maha-desktop kernel: [    0.692491] bus: 04 index 0 io port: [9000, 9fff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692494] bus: 04 index 1 mmio: [fda00000, fdafffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692507] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692510] bus: 04 index 3 io port: [0, ffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692512] bus: 04 index 4 mmio: [0, ffffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692515] bus: 80 index 0 io port: [0, ffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692518] bus: 80 index 1 mmio: [0, ffffffff]
Mar 18 04:58:57 maha-desktop kernel: [    0.692532] NET: Registered protocol family 2
Mar 18 04:58:57 maha-desktop kernel: [    0.704595] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.704975] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.705406] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    0.705691] TCP: Hash tables configured (established 131072 bind 65536)
Mar 18 04:58:57 maha-desktop kernel: [    0.705695] TCP reno registered
Mar 18 04:58:57 maha-desktop kernel: [    0.708649] NET: Registered protocol family 1
Mar 18 04:58:57 maha-desktop kernel: [    0.708806] checking if image is initramfs... it is
Mar 18 04:58:57 maha-desktop kernel: [    1.443953] Freeing initrd memory: 8503k freed
Mar 18 04:58:57 maha-desktop kernel: [    1.445838] audit: initializing netlink socket (disabled)
Mar 18 04:58:57 maha-desktop kernel: [    1.445857] type=2000 audit(1237352313.444:1): initialized
Mar 18 04:58:57 maha-desktop kernel: [    1.451240] highmem bounce pool size: 64 pages
Mar 18 04:58:57 maha-desktop kernel: [    1.451250] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 18 04:58:57 maha-desktop kernel: [    1.455272] VFS: Disk quotas dquot_6.5.1
Mar 18 04:58:57 maha-desktop kernel: [    1.455413] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 18 04:58:57 maha-desktop kernel: [    1.455572] msgmni has been set to 1743
Mar 18 04:58:57 maha-desktop kernel: [    1.455771] io scheduler noop registered
Mar 18 04:58:57 maha-desktop kernel: [    1.455775] io scheduler anticipatory registered
Mar 18 04:58:57 maha-desktop kernel: [    1.455778] io scheduler deadline registered
Mar 18 04:58:57 maha-desktop kernel: [    1.455795] io scheduler cfq registered (default)
Mar 18 04:58:57 maha-desktop kernel: [    1.455818] PCI: VIA PCI bridge detected.Disabling DAC.
Mar 18 04:58:57 maha-desktop kernel: [    1.455943] pci 0000:02:00.0: Boot video device
Mar 18 04:58:57 maha-desktop kernel: [    1.456158] pcieport-driver 0000:00:02.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    1.456211] pcieport-driver 0000:00:02.0: found MSI capability
Mar 18 04:58:57 maha-desktop kernel: [    1.456271] pci_express 0000:00:02.0:pcie00: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456347] pci_express 0000:00:02.0:pcie01: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456434] pci_express 0000:00:02.0:pcie02: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456519] pci_express 0000:00:02.0:pcie03: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456671] pcieport-driver 0000:00:03.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [    1.456729] pcieport-driver 0000:00:03.0: found MSI capability
Mar 18 04:58:57 maha-desktop kernel: [    1.456795] pci_express 0000:00:03.0:pcie00: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456867] pci_express 0000:00:03.0:pcie01: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.456948] pci_express 0000:00:03.0:pcie02: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.457025] pci_express 0000:00:03.0:pcie03: allocate port service
Mar 18 04:58:57 maha-desktop kernel: [    1.462602] aer 0000:00:02.0:pcie01: service driver aer loaded
Mar 18 04:58:57 maha-desktop kernel: [    1.467813] aer 0000:00:03.0:pcie01: service driver aer loaded
Mar 18 04:58:57 maha-desktop kernel: [    1.468232] isapnp: Scanning for PnP cards...
Mar 18 04:58:57 maha-desktop kernel: [    1.822320] isapnp: No Plug & Play device found
Mar 18 04:58:57 maha-desktop kernel: [    1.881518] hpet_resources: 0xfe800000 is busy
Mar 18 04:58:57 maha-desktop kernel: [    1.881625] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 18 04:58:57 maha-desktop kernel: [    1.881791] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 18 04:58:57 maha-desktop kernel: [    1.882852] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 18 04:58:57 maha-desktop kernel: [    1.886000] brd: module loaded
Mar 18 04:58:57 maha-desktop kernel: [    1.886118] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 18 04:58:57 maha-desktop kernel: [    1.886342] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 18 04:58:57 maha-desktop kernel: [    1.886812] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 18 04:58:57 maha-desktop kernel: [    1.886823] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 18 04:58:57 maha-desktop kernel: [    1.888208] mice: PS/2 mouse device common for all mice
Mar 18 04:58:57 maha-desktop kernel: [    1.888430] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar 18 04:58:57 maha-desktop kernel: [    1.888470] rtc0: alarms up to one year, y3k, hpet irqs
Mar 18 04:58:57 maha-desktop kernel: [    1.888713] EISA: Probing bus 0 at eisa.0
Mar 18 04:58:57 maha-desktop kernel: [    1.888760] EISA: Detected 0 cards.
Mar 18 04:58:57 maha-desktop kernel: [    1.888764] cpuidle: using governor ladder
Mar 18 04:58:57 maha-desktop kernel: [    1.888767] cpuidle: using governor menu
Mar 18 04:58:57 maha-desktop kernel: [    1.889551] TCP cubic registered
Mar 18 04:58:57 maha-desktop kernel: [    1.889596] Using IPI No-Shortcut mode
Mar 18 04:58:57 maha-desktop kernel: [    1.889924] registered taskstats version 1
Mar 18 04:58:57 maha-desktop kernel: [    1.890106]   Magic number: 1:198:970
Mar 18 04:58:57 maha-desktop kernel: [    1.890273] rtc_cmos 00:07: setting system clock to 2009-03-18 04:58:34 UTC (1237352314)
Mar 18 04:58:57 maha-desktop kernel: [    1.890278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 18 04:58:57 maha-desktop kernel: [    1.890280] EDD information not available.
Mar 18 04:58:57 maha-desktop kernel: [    1.890583] Freeing unused kernel memory: 424k freed
Mar 18 04:58:57 maha-desktop kernel: [    1.890649] Write protecting the kernel text: 2580k
Mar 18 04:58:57 maha-desktop kernel: [    1.890688] Write protecting the kernel read-only data: 940k
Mar 18 04:58:57 maha-desktop kernel: [    1.912122] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 18 04:58:57 maha-desktop kernel: [    2.120137] fuse init (API version 7.9)
Mar 18 04:58:57 maha-desktop kernel: [    2.208046] fan PNP0C0B:00: registered as cooling_device0
Mar 18 04:58:57 maha-desktop kernel: [    2.208059] ACPI: Fan [FAN] (on)
Mar 18 04:58:57 maha-desktop kernel: [    2.240045] processor ACPI0007:00: registered as cooling_device1
Mar 18 04:58:57 maha-desktop kernel: [    2.244040] processor ACPI0007:01: registered as cooling_device2
Mar 18 04:58:57 maha-desktop kernel: [    2.264075] thermal LNXTHERM:01: registered as thermal_zone0
Mar 18 04:58:57 maha-desktop kernel: [    2.264696] ACPI: Thermal Zone [THRM] (56 C)
Mar 18 04:58:57 maha-desktop kernel: [    2.324045] device-mapper: uevent: version 1.0.3
Mar 18 04:58:57 maha-desktop kernel: [    2.324391] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Mar 18 04:58:57 maha-desktop kernel: [    3.304415] No dock devices found.
Mar 18 04:58:57 maha-desktop kernel: [    3.392807] SCSI subsystem initialized
Mar 18 04:58:57 maha-desktop kernel: [    3.463600] usbcore: registered new interface driver usbfs
Mar 18 04:58:57 maha-desktop kernel: [    3.463656] usbcore: registered new interface driver hub
Mar 18 04:58:57 maha-desktop kernel: [    3.468579] usbcore: registered new device driver usb
Mar 18 04:58:57 maha-desktop kernel: [    3.580697] USB Universal Host Controller Interface driver v3.0
Mar 18 04:58:57 maha-desktop kernel: [    3.580838] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar 18 04:58:57 maha-desktop kernel: [    3.580855] uhci_hcd 0000:00:10.0: UHCI Host Controller
Mar 18 04:58:57 maha-desktop kernel: [    3.580934] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Mar 18 04:58:57 maha-desktop kernel: [    3.580976] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
Mar 18 04:58:57 maha-desktop kernel: [    3.581230] usb usb1: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    3.581286] hub 1-0:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    3.581299] hub 1-0:1.0: 2 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    3.607228] libata version 3.00 loaded.
Mar 18 04:58:57 maha-desktop kernel: [    3.644672] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar 18 04:58:57 maha-desktop kernel: [    3.678324] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Mar 18 04:58:57 maha-desktop kernel: [    3.678333] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Mar 18 04:58:57 maha-desktop kernel: [    3.793060] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Mar 18 04:58:57 maha-desktop kernel: [    3.793080] uhci_hcd 0000:00:10.1: UHCI Host Controller
Mar 18 04:58:57 maha-desktop kernel: [    3.793145] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Mar 18 04:58:57 maha-desktop kernel: [    3.793197] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
Mar 18 04:58:57 maha-desktop kernel: [    3.793429] usb usb2: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    3.793493] hub 2-0:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    3.793508] hub 2-0:1.0: 2 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    3.904163] usb 1-1: new full speed USB device using uhci_hcd and address 2
Mar 18 04:58:57 maha-desktop kernel: [    4.001010] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Mar 18 04:58:57 maha-desktop kernel: [    4.001029] uhci_hcd 0000:00:10.2: UHCI Host Controller
Mar 18 04:58:57 maha-desktop kernel: [    4.001089] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Mar 18 04:58:57 maha-desktop kernel: [    4.001139] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
Mar 18 04:58:57 maha-desktop kernel: [    4.001360] usb usb3: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    4.001422] hub 3-0:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    4.001437] hub 3-0:1.0: 2 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    4.077307] usb 1-1: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    4.080125] hub 1-1:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    4.082047] hub 1-1:1.0: 3 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    4.208959] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Mar 18 04:58:57 maha-desktop kernel: [    4.208977] uhci_hcd 0000:00:10.3: UHCI Host Controller
Mar 18 04:58:57 maha-desktop kernel: [    4.209037] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Mar 18 04:58:57 maha-desktop kernel: [    4.209087] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
Mar 18 04:58:57 maha-desktop kernel: [    4.209309] usb usb4: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    4.209389] hub 4-0:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    4.209409] hub 4-0:1.0: 2 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    4.369039] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
Mar 18 04:58:57 maha-desktop kernel: [    4.416483] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 18 04:58:57 maha-desktop kernel: [    4.416553] pata_acpi 0000:00:0f.0: PCI INT B disabled
Mar 18 04:58:57 maha-desktop kernel: [    4.416584] pata_via 0000:00:0f.1: version 0.3.3
Mar 18 04:58:57 maha-desktop kernel: [    4.416748] scsi0 : pata_via
Mar 18 04:58:57 maha-desktop kernel: [    4.416878] scsi1 : pata_via
Mar 18 04:58:57 maha-desktop kernel: [    4.419901] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
Mar 18 04:58:57 maha-desktop kernel: [    4.419905] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
Mar 18 04:58:57 maha-desktop kernel: [    4.507222] usb 1-1.1: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    4.588589] ata1.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
Mar 18 04:58:57 maha-desktop kernel: [    4.588595] ata1.00: 240121728 sectors, multi 16: LBA 
Mar 18 04:58:57 maha-desktop kernel: [    4.599672] ata1.01: ATA-8: WDC WD5000AAKB-00YSA0, 12.01C02, max UDMA/100
Mar 18 04:58:57 maha-desktop kernel: [    4.599676] ata1.01: 976773168 sectors, multi 16: LBA48 
Mar 18 04:58:57 maha-desktop kernel: [    4.612453] ata1.00: configured for UDMA/133
Mar 18 04:58:57 maha-desktop kernel: [    4.628622] ata1.01: configured for UDMA/100
Mar 18 04:58:57 maha-desktop kernel: [    4.800385] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
Mar 18 04:58:57 maha-desktop kernel: [    4.800421] ata2.01: ATAPI: CD-ROM CDU701-F, 1.0r, max MWDMA2
Mar 18 04:58:57 maha-desktop kernel: [    4.816268] ata2.00: configured for UDMA/33
Mar 18 04:58:57 maha-desktop kernel: [    4.832262] ata2.01: configured for MWDMA2
Mar 18 04:58:57 maha-desktop kernel: [    4.832424] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
Mar 18 04:58:57 maha-desktop kernel: [    4.832645] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 12.0 PQ: 0 ANSI: 5
Mar 18 04:58:57 maha-desktop kernel: [    4.836411] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
Mar 18 04:58:57 maha-desktop kernel: [    4.837390] scsi 1:0:1:0: CD-ROM            SONY     CD-ROM CDU701-F  1.0r PQ: 0 ANSI: 5
Mar 18 04:58:57 maha-desktop kernel: [    4.837666] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Mar 18 04:58:57 maha-desktop kernel: [    4.837688] ehci_hcd 0000:00:10.4: EHCI Host Controller
Mar 18 04:58:57 maha-desktop kernel: [    4.837757] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Mar 18 04:58:57 maha-desktop kernel: [    4.837813] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
Mar 18 04:58:57 maha-desktop kernel: [    4.848512] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 18 04:58:57 maha-desktop kernel: [    4.848718] usb usb5: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    4.848762] hub 5-0:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    4.848775] hub 5-0:1.0: 8 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    4.864558] usb 1-1: USB disconnect, address 2
Mar 18 04:58:57 maha-desktop kernel: [    4.864562] usb 1-1.1: USB disconnect, address 3
Mar 18 04:58:57 maha-desktop kernel: [    5.056403] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 18 04:58:57 maha-desktop kernel: [    5.060779] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:7b:51:0c, IRQ 23.
Mar 18 04:58:57 maha-desktop kernel: [    5.061489] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
Mar 18 04:58:57 maha-desktop kernel: [    5.095277] sata_via 0000:00:0f.0: version 2.3
Mar 18 04:58:57 maha-desktop kernel: [    5.095302] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 18 04:58:57 maha-desktop kernel: [    5.095369] sata_via 0000:00:0f.0: routed to hard irq line 11
Mar 18 04:58:57 maha-desktop kernel: [    5.095972] scsi2 : sata_via
Mar 18 04:58:57 maha-desktop kernel: [    5.099201] scsi3 : sata_via
Mar 18 04:58:57 maha-desktop kernel: [    5.103712] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Mar 18 04:58:57 maha-desktop kernel: [    5.103801] scsi 0:0:1:0: Attached scsi generic sg1 type 0
Mar 18 04:58:57 maha-desktop kernel: [    5.103893] scsi 1:0:0:0: Attached scsi generic sg2 type 5
Mar 18 04:58:57 maha-desktop kernel: [    5.103975] scsi 1:0:1:0: Attached scsi generic sg3 type 5
Mar 18 04:58:57 maha-desktop kernel: [    5.104979] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
Mar 18 04:58:57 maha-desktop kernel: [    5.104986] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
Mar 18 04:58:57 maha-desktop kernel: [    5.133877] Driver 'sd' needs updating - please use bus_type methods
Mar 18 04:58:57 maha-desktop kernel: [    5.135758] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Mar 18 04:58:57 maha-desktop kernel: [    5.135804] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 04:58:57 maha-desktop kernel: [    5.135812] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 04:58:57 maha-desktop kernel: [    5.135887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 04:58:57 maha-desktop kernel: [    5.136069] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Mar 18 04:58:57 maha-desktop kernel: [    5.136103] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 04:58:57 maha-desktop kernel: [    5.136108] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 04:58:57 maha-desktop kernel: [    5.136164] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 04:58:57 maha-desktop kernel: [    5.136173]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Mar 18 04:58:57 maha-desktop kernel: [    5.155338]  sda1
Mar 18 04:58:57 maha-desktop kernel: [    5.155509] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 18 04:58:57 maha-desktop kernel: [    5.155636] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Mar 18 04:58:57 maha-desktop kernel: [    5.155665] sd 0:0:1:0: [sdb] Write Protect is off
Mar 18 04:58:57 maha-desktop kernel: [    5.155669] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Mar 18 04:58:57 maha-desktop kernel: [    5.155715] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 04:58:57 maha-desktop kernel: [    5.155811] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Mar 18 04:58:57 maha-desktop kernel: [    5.155837] sd 0:0:1:0: [sdb] Write Protect is off
Mar 18 04:58:57 maha-desktop kernel: [    5.155841] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Mar 18 04:58:57 maha-desktop kernel: [    5.155887] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 04:58:57 maha-desktop kernel: [    5.155893]  sdb: sdb1 sdb2 sdb3 sdb4
Mar 18 04:58:57 maha-desktop kernel: [    5.171158] sd 0:0:1:0: [sdb] Attached SCSI disk
Mar 18 04:58:57 maha-desktop kernel: [    5.183476] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 18 04:58:57 maha-desktop kernel: [    5.183486] Uniform CD-ROM driver Revision: 3.20
Mar 18 04:58:57 maha-desktop kernel: [    5.183649] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 18 04:58:57 maha-desktop kernel: [    5.186374] sr1: scsi3-mmc drive: 14x/32x cd/rw xa/form2 cdda tray
Mar 18 04:58:57 maha-desktop kernel: [    5.186503] sr 1:0:1:0: Attached scsi CD-ROM sr1
Mar 18 04:58:57 maha-desktop kernel: [    5.308022] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar 18 04:58:57 maha-desktop kernel: [    5.512015] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar 18 04:58:57 maha-desktop kernel: [    5.600887] usb 1-1: new full speed USB device using uhci_hcd and address 4
Mar 18 04:58:57 maha-desktop kernel: [    5.782265] usb 1-1: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    5.785115] hub 1-1:1.0: USB hub found
Mar 18 04:58:57 maha-desktop kernel: [    5.787075] hub 1-1:1.0: 3 ports detected
Mar 18 04:58:57 maha-desktop kernel: [    6.040532] PM: Starting manual resume from disk
Mar 18 04:58:57 maha-desktop kernel: [    6.040538] PM: Resume from partition 8:19
Mar 18 04:58:57 maha-desktop kernel: [    6.040541] PM: Checking hibernation image.
Mar 18 04:58:57 maha-desktop kernel: [    6.040762] PM: Resume from disk failed.
Mar 18 04:58:57 maha-desktop kernel: [    6.069006] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 18 04:58:57 maha-desktop kernel: [    6.069014] EXT3-fs: write access will be enabled during recovery.
Mar 18 04:58:57 maha-desktop kernel: [    6.078072] usb 1-1.1: new full speed USB device using uhci_hcd and address 5
Mar 18 04:58:57 maha-desktop kernel: [    6.215279] usb 1-1.1: configuration #1 chosen from 1 choice
Mar 18 04:58:57 maha-desktop kernel: [    7.301451] kjournald starting.  Commit interval 5 seconds
Mar 18 04:58:57 maha-desktop kernel: [    7.301467] EXT3-fs: sdb2: orphan cleanup on readonly fs
Mar 18 04:58:57 maha-desktop kernel: [    7.301477] ext3_orphan_cleanup: deleting unreferenced inode 5128767
Mar 18 04:58:57 maha-desktop kernel: [    7.301541] ext3_orphan_cleanup: deleting unreferenced inode 557145
Mar 18 04:58:57 maha-desktop kernel: [    7.301568] ext3_orphan_cleanup: deleting unreferenced inode 5128761
Mar 18 04:58:57 maha-desktop kernel: [    7.311756] ext3_orphan_cleanup: deleting unreferenced inode 4120637
Mar 18 04:58:57 maha-desktop kernel: [    7.321750] ext3_orphan_cleanup: deleting unreferenced inode 4120633
Mar 18 04:58:57 maha-desktop kernel: [    7.321971] ext3_orphan_cleanup: deleting unreferenced inode 4120612
Mar 18 04:58:57 maha-desktop kernel: [    7.321994] ext3_orphan_cleanup: deleting unreferenced inode 4120635
Mar 18 04:58:57 maha-desktop kernel: [    7.336344] ext3_orphan_cleanup: deleting unreferenced inode 4120579
Mar 18 04:58:57 maha-desktop kernel: [    7.336366] ext3_orphan_cleanup: deleting unreferenced inode 4120583
Mar 18 04:58:57 maha-desktop kernel: [    7.356505] ext3_orphan_cleanup: deleting unreferenced inode 2377748
Mar 18 04:58:57 maha-desktop kernel: [    7.371307] ext3_orphan_cleanup: deleting unreferenced inode 2377716
Mar 18 04:58:57 maha-desktop kernel: [    7.374260] ext3_orphan_cleanup: deleting unreferenced inode 2377750
Mar 18 04:58:57 maha-desktop kernel: [    7.374487] ext3_orphan_cleanup: deleting unreferenced inode 2377730
Mar 18 04:58:57 maha-desktop kernel: [    7.374510] ext3_orphan_cleanup: deleting unreferenced inode 2377736
Mar 18 04:58:57 maha-desktop kernel: [    7.374727] ext3_orphan_cleanup: deleting unreferenced inode 2375735
Mar 18 04:58:57 maha-desktop kernel: [    7.383455] ext3_orphan_cleanup: deleting unreferenced inode 2375714
Mar 18 04:58:57 maha-desktop kernel: [    7.391798] ext3_orphan_cleanup: deleting unreferenced inode 2375713
Mar 18 04:58:57 maha-desktop kernel: [    7.392022] ext3_orphan_cleanup: deleting unreferenced inode 2375711
Mar 18 04:58:57 maha-desktop kernel: [    7.406936] ext3_orphan_cleanup: deleting unreferenced inode 2375710
Mar 18 04:58:57 maha-desktop kernel: [    7.424730] ext3_orphan_cleanup: deleting unreferenced inode 557077
Mar 18 04:58:57 maha-desktop kernel: [    7.424745] EXT3-fs: sdb2: 20 orphan inodes deleted
Mar 18 04:58:57 maha-desktop kernel: [    7.424748] EXT3-fs: recovery complete.
Mar 18 04:58:57 maha-desktop kernel: [    7.454624] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 04:58:57 maha-desktop kernel: [   12.313393] udevd version 124 started
Mar 18 04:58:57 maha-desktop kernel: [   12.696331] Linux agpgart interface v0.103
Mar 18 04:58:57 maha-desktop kernel: [   12.736208] agpgart: Detected VIA P4M900 chipset
Mar 18 04:58:57 maha-desktop kernel: [   12.777282] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Mar 18 04:58:57 maha-desktop kernel: [   13.128232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 18 04:58:57 maha-desktop kernel: [   13.188330] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 18 04:58:57 maha-desktop kernel: [   13.413855] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 18 04:58:57 maha-desktop kernel: [   13.428542] ACPI: Power Button (FF) [PWRF]
Mar 18 04:58:57 maha-desktop kernel: [   13.428708] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Mar 18 04:58:57 maha-desktop kernel: [   13.460570] ACPI: Power Button (CM) [PWRB]
Mar 18 04:58:57 maha-desktop kernel: [   13.460760] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Mar 18 04:58:57 maha-desktop kernel: [   13.484543] ACPI: Sleep Button (CM) [SLPB]
Mar 18 04:58:57 maha-desktop kernel: [   14.458475] parport_pc 00:0c: reported by Plug and Play ACPI
Mar 18 04:58:57 maha-desktop kernel: [   14.458532] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 18 04:58:57 maha-desktop kernel: [   15.392035] nvidia: module license 'NVIDIA' taints kernel.
Mar 18 04:58:57 maha-desktop kernel: [   15.964807] input: PC Speaker as /devices/platform/pcspkr/input/input5
Mar 18 04:58:57 maha-desktop kernel: [   16.147852] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Mar 18 04:58:57 maha-desktop kernel: [   16.147865] nvidia 0000:02:00.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [   16.148159] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
Mar 18 04:58:57 maha-desktop kernel: [   16.248288] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Mar 18 04:58:57 maha-desktop kernel: [   16.310955] device-mapper: multipath: version 1.0.5 loaded
Mar 18 04:58:57 maha-desktop kernel: [   17.011762] Bluetooth: Core ver 2.13
Mar 18 04:58:57 maha-desktop kernel: [   17.014939] NET: Registered protocol family 31
Mar 18 04:58:57 maha-desktop kernel: [   17.014945] Bluetooth: HCI device and connection manager initialized
Mar 18 04:58:57 maha-desktop kernel: [   17.014951] Bluetooth: HCI socket layer initialized
Mar 18 04:58:57 maha-desktop kernel: [   17.136739] Bluetooth: Generic Bluetooth USB driver ver 0.3
Mar 18 04:58:57 maha-desktop kernel: [   17.137164] usbcore: registered new interface driver btusb
Mar 18 04:58:57 maha-desktop kernel: [   17.244814] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
Mar 18 04:58:57 maha-desktop kernel: [   17.245324] ndiswrapper 0000:04:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 04:58:57 maha-desktop kernel: [   17.699446] ndiswrapper: using IRQ 17
Mar 18 04:58:57 maha-desktop kernel: [   17.831369] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Mar 18 04:58:57 maha-desktop kernel: [   18.341411] wlan0: ethernet device 00:19:5b:53:bd:95 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
Mar 18 04:58:57 maha-desktop kernel: [   18.471606] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Mar 18 04:58:57 maha-desktop kernel: [   18.475990] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 04:58:57 maha-desktop kernel: [   18.476050] HDA Intel 0000:80:01.0: setting latency timer to 64
Mar 18 04:58:57 maha-desktop kernel: [   18.476059] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
Mar 18 04:58:57 maha-desktop kernel: [   18.485064] usbcore: registered new interface driver ndiswrapper
Mar 18 04:58:57 maha-desktop kernel: [   20.204563] lp0: using parport0 (interrupt-driven).
Mar 18 04:58:57 maha-desktop kernel: [   20.398365] Adding 1574360k swap on /dev/sdb3.  Priority:-1 extents:1 across:1574360k
Mar 18 04:58:57 maha-desktop kernel: [   20.972069] EXT3 FS on sdb2, internal journal
Mar 18 04:58:57 maha-desktop kernel: [   23.010371] type=1505 audit(1237366735.944:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4409
Mar 18 04:58:57 maha-desktop kernel: [   23.214410] type=1505 audit(1237366736.148:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4414
Mar 18 04:58:57 maha-desktop kernel: [   23.214687] type=1505 audit(1237366736.148:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4414
Mar 18 04:58:57 maha-desktop kernel: [   23.386338] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 18 04:58:57 maha-desktop kernel: [   24.144090] ACPI: WMI: Mapper loaded
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Successfully dropped root privileges.
Mar 18 04:58:58 maha-desktop kernel: [   25.192089] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: avahi-daemon 0.6.23 starting up.
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Successfully called chroot().
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Successfully dropped remaining capabilities.
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: No service file found in /etc/avahi/services.
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Network interface enumeration completed.
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 18 04:58:58 maha-desktop avahi-daemon[5038]: Server startup complete. Host name is maha-desktop.local. Local service cookie is 674909888.
Mar 18 04:58:58 maha-desktop kernel: [   25.249988] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 18 04:58:58 maha-desktop kernel: [   25.250002] apm: disabled - APM is not SMP safe.
Mar 18 04:58:58 maha-desktop kernel: [   25.381221] ppdev: user-space parallel port driver
Mar 18 04:58:58 maha-desktop kernel: [   25.525228] NET: Registered protocol family 10
Mar 18 04:58:58 maha-desktop kernel: [   25.528060] lo: Disabled Privacy Extensions
Mar 18 04:59:00 maha-desktop kernel: [   27.351032] Bridge firewalling registered
Mar 18 04:59:00 maha-desktop avahi-daemon[5038]: Joining mDNS multicast group on interface vnet0.IPv4 with address 192.168.122.1.
Mar 18 04:59:00 maha-desktop kernel: [   27.380523] vnet0: starting userspace STP failed, starting kernel STP
Mar 18 04:59:00 maha-desktop avahi-daemon[5038]: New relevant interface vnet0.IPv4 for mDNS.
Mar 18 04:59:00 maha-desktop avahi-daemon[5038]: Registering new address record for 192.168.122.1 on vnet0.IPv4.
Mar 18 04:59:00 maha-desktop kernel: [   27.747639] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 18 04:59:00 maha-desktop kernel: [   27.749178] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
Mar 18 04:59:00 maha-desktop kernel: [   27.749189] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Mar 18 04:59:00 maha-desktop kernel: [   27.749195] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: started, version 2.45 cachesize 150
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: compile time options: IPv6 GNU-getopt no-ISC-leasefile DBus I18N TFTP
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: reading /etc/resolv.conf
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: using nameserver 192.168.0.1#53
Mar 18 04:59:01 maha-desktop dnsmasq[5511]: read /etc/hosts - 8 addresses
Mar 18 04:59:01 maha-desktop avahi-daemon[5038]: Registering new address record for fe80::a07d:b5ff:fea5:5c5b on vnet0.*.
Mar 18 04:59:02 maha-desktop kernel: [   29.927713] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Mar 18 04:59:02 maha-desktop kernel: [   29.927722] vboxdrv: Successfully done.
Mar 18 04:59:02 maha-desktop kernel: [   29.927725] vboxdrv: Found 2 processor cores.
Mar 18 04:59:02 maha-desktop kernel: [   29.929171] vboxdrv: fAsync=0 offMin=0x61f offMax=0x24f9
Mar 18 04:59:02 maha-desktop kernel: [   29.930284] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Mar 18 04:59:02 maha-desktop kernel: [   29.930295] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
Mar 18 04:59:04 maha-desktop kernel: [   31.737347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 04:59:04 maha-desktop xinetd[5722]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Mar 18 04:59:04 maha-desktop xinetd[5722]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Mar 18 04:59:04 maha-desktop xinetd[5722]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Mar 18 04:59:04 maha-desktop xinetd[5722]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Mar 18 04:59:04 maha-desktop xinetd[5722]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing chargen
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing chargen
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing daytime
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing daytime
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing discard
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing discard
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing echo
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing echo
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing time
Mar 18 04:59:05 maha-desktop xinetd[5722]: removing time
Mar 18 04:59:05 maha-desktop xinetd[5722]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Mar 18 04:59:05 maha-desktop xinetd[5722]: Started working: 0 available services
Mar 18 04:59:05 maha-desktop acpid: client connected from 5747[111:122] 
Mar 18 04:59:05 maha-desktop bluetoothd[5800]: Bluetooth daemon
Mar 18 04:59:05 maha-desktop bluetoothd[5800]: Starting SDP server
Mar 18 04:59:05 maha-desktop kernel: [   33.044190] Bluetooth: L2CAP ver 2.11
Mar 18 04:59:05 maha-desktop kernel: [   33.044197] Bluetooth: L2CAP socket layer initialized
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: bridge pan0 created
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Starting experimental netlink support
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Failed to find Bluetooth netlink family
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 18 04:59:06 maha-desktop kernel: [   33.066655] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 18 04:59:06 maha-desktop kernel: [   33.066664] Bluetooth: BNEP filters: protocol multicast
Mar 18 04:59:06 maha-desktop kernel: [   33.083249] Bluetooth: SCO (Voice Link) ver 0.6
Mar 18 04:59:06 maha-desktop kernel: [   33.083256] Bluetooth: SCO socket layer initialized
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: HCI dev 0 registered
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: HCI dev 0 up
Mar 18 04:59:06 maha-desktop kernel: [   33.215284] Bluetooth: RFCOMM socket layer initialized
Mar 18 04:59:06 maha-desktop kernel: [   33.217303] Bluetooth: RFCOMM TTY layer initialized
Mar 18 04:59:06 maha-desktop kernel: [   33.217315] Bluetooth: RFCOMM ver 1.10
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Registered interface org.bluez.NetworkPeer on path /org/bluez/hci0
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Registered interface org.bluez.NetworkHub on path /org/bluez/hci0
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Registered interface org.bluez.NetworkRouter on path /org/bluez/hci0
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Registered interface org.bluez.Service on path /org/bluez/hci0
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/hci0
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Adapter /org/bluez/hci0 has been enabled
Mar 18 04:59:06 maha-desktop bluetoothd[5800]: Starting security manager 0
Mar 18 04:59:07 maha-desktop acpid: client connected from 5868[0:0] 
Mar 18 04:59:08 maha-desktop kernel: [   35.210665] eth0: link down
Mar 18 04:59:08 maha-desktop kernel: [   35.211182] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 18 04:59:09 maha-desktop anacron[5905]: Anacron 2.3 started on 2009-03-18
Mar 18 04:59:09 maha-desktop anacron[5905]: Will run job `cron.daily' in 5 min.
Mar 18 04:59:09 maha-desktop anacron[5905]: Jobs will be executed sequentially
Mar 18 04:59:09 maha-desktop /usr/sbin/cron[5951]: (CRON) INFO (pidfile fd = 3)
Mar 18 04:59:09 maha-desktop /usr/sbin/cron[5952]: (CRON) STARTUP (fork ok)
Mar 18 04:59:09 maha-desktop /usr/sbin/cron[5952]: (CRON) INFO (Running @reboot jobs)
Mar 18 04:59:09 maha-desktop acpid: client connected from 5868[0:0] 
Mar 18 04:59:10 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 18 04:59:10 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 18 04:59:10 maha-desktop dhclient: All rights reserved.
Mar 18 04:59:10 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 18 04:59:10 maha-desktop dhclient: 
Mar 18 04:59:10 maha-desktop kernel: [   37.444011] vnet0: no IPv6 routers present
Mar 18 04:59:10 maha-desktop kernel: [   37.547071] NET: Registered protocol family 17
Mar 18 04:59:10 maha-desktop dhclient: Bind socket to interface: No such device
Mar 18 04:59:10 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 18 04:59:10 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 18 04:59:10 maha-desktop dhclient: All rights reserved.
Mar 18 04:59:10 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 18 04:59:10 maha-desktop dhclient: 
Mar 18 04:59:10 maha-desktop dhclient: Bind socket to interface: No such device
Mar 18 04:59:10 maha-desktop kernel: [   37.678416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 04:59:11 maha-desktop kernel: [   38.411737] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 18 04:59:11 maha-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 18 04:59:11 maha-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 18 04:59:11 maha-desktop dhclient: All rights reserved.
Mar 18 04:59:11 maha-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 18 04:59:11 maha-desktop dhclient: 
Mar 18 04:59:12 maha-desktop dhclient: Listening on LPF/wlan0/00:19:5b:53:bd:95
Mar 18 04:59:12 maha-desktop dhclient: Sending on   LPF/wlan0/00:19:5b:53:bd:95
Mar 18 04:59:12 maha-desktop dhclient: Sending on   Socket/fallback
Mar 18 04:59:13 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 18 04:59:13 maha-desktop avahi-daemon[5038]: Registering new address record for fe80::219:5bff:fe53:bd95 on wlan0.*.
Mar 18 04:59:13 maha-desktop pulseaudio[6277]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 18 04:59:13 maha-desktop pulseaudio[6279]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 18 04:59:13 maha-desktop pulseaudio[6279]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 18 04:59:14 maha-desktop kernel: [   41.090809] hda-intel: Invalid position buffer, using LPIB read method instead.
Mar 18 04:59:14 maha-desktop kernel: [   41.090854] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Mar 18 04:59:20 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 18 04:59:22 maha-desktop kernel: [   49.292024] wlan0: no IPv6 routers present
Mar 18 04:59:29 maha-desktop x-session-manager[6214]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Mar 18 04:59:33 maha-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Mar 18 04:59:33 maha-desktop dhclient: DHCPOFFER of 192.168.0.158 from 192.168.0.1
Mar 18 04:59:33 maha-desktop dhclient: DHCPREQUEST of 192.168.0.158 on wlan0 to 255.255.255.255 port 67
Mar 18 04:59:33 maha-desktop dhclient: DHCPACK of 192.168.0.158 from 192.168.0.1
Mar 18 04:59:33 maha-desktop avahi-daemon[5038]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.158.
Mar 18 04:59:33 maha-desktop avahi-daemon[5038]: New relevant interface wlan0.IPv4 for mDNS.
Mar 18 04:59:33 maha-desktop avahi-daemon[5038]: Registering new address record for 192.168.0.158 on wlan0.IPv4.
Mar 18 04:59:33 maha-desktop dhclient: bound to 192.168.0.158 -- renewal in 36713 seconds.
Mar 18 04:59:39 maha-desktop x-session-manager[6214]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 18 04:59:39 maha-desktop x-session-manager[6214]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory) 
Mar 18 04:59:39 maha-desktop pulseaudio[6279]: module-x11-xsmp.c: X11 session manager not running.
Mar 18 04:59:39 maha-desktop pulseaudio[6279]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 18 05:00:01 maha-desktop /USR/SBIN/CRON[6597]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 05:00:53 maha-desktop kernel: [  140.328579] ppdev0: registered pardevice
Mar 18 05:00:53 maha-desktop kernel: [  140.376546] ppdev0: unregistered pardevice
Mar 18 05:00:54 maha-desktop kernel: [  141.690475] Too big adjustment 32
Mar 18 05:00:54 maha-desktop kernel: [  141.736100] Too big adjustment 32
Mar 18 05:00:54 maha-desktop kernel: [  141.953068] ppdev0: registered pardevice
Mar 18 05:00:54 maha-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 18 05:00:54 maha-desktop kernel: [  142.001007] ppdev0: unregistered pardevice
Mar 18 05:00:57 maha-desktop kernel: [  144.168643] ppdev0: registered pardevice
Mar 18 05:00:57 maha-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 18 05:00:57 maha-desktop kernel: [  144.216689] ppdev0: unregistered pardevice
Mar 18 05:04:09 maha-desktop anacron[5905]: Job `cron.daily' started
Mar 18 05:04:09 maha-desktop anacron[7059]: Updated timestamp for job `cron.daily' to 2009-03-18
Mar 18 05:05:01 maha-desktop /USR/SBIN/CRON[7127]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 05:10:01 maha-desktop /USR/SBIN/CRON[7398]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 05:15:01 maha-desktop /USR/SBIN/CRON[7648]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Mar 18 05:17:01 maha-desktop /USR/SBIN/CRON[7776]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 05:20:01 maha-desktop /USR/SBIN/CRON[7969]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)

```

---

### Post by mahasmb on 2009-03-18
My dmesg file:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 377a2000 - 37fefd91
[    0.000000] ACPI: RSDP 000F7F50, 0014 (r0 P4M900)
[    0.000000] ACPI: RSDT 7FEE3000, 0034 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE3080, 0074 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3100, 62D0 (r1 P4M900 AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE94C0, 0038 (r1 P4M900 AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEE9500, 003C (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE9400, 0090 (r1 P4M900 AWRDACPI 42302E31 AWRD        0)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [00377a2000 - 0037fefd91]          RAMDISK ==> [00377a2000 - 0037fefd91]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f3d60] 000f3d60
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292034 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 5, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519281
[    0.000000] Kernel command line: root=UUID=fab527b5-514d-4898-9584-cd6a6f071a5c ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2999.923 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2061984k/2096000k available (2576k kernel code, 32852k reserved, 1165k data, 424k init, 1178496k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.84 BogoMIPS (lpj=11999692)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018664] ACPI: Core revision 20080609
[    0.022419] ACPI: Checking initramfs for custom DSDT
[    0.372417] ENABLING IO-APIC IRQs
[    0.372608] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.414544] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.416026] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5999.85 BogoMIPS (lpj=11999708)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.500434] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.500463] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.504061] Brought up 2 CPUs
[    0.504067] Total of 2 processors activated (11999.70 BogoMIPS).
[    0.504092] CPU0 attaching sched-domain:
[    0.504096]  domain 0: span 0-1 level SIBLING
[    0.504100]   groups: 0 1
[    0.504109] CPU1 attaching sched-domain:
[    0.504112]  domain 0: span 0-1 level SIBLING
[    0.504116]   groups: 1 0
[    0.504216] net_namespace: 840 bytes
[    0.504216] Booting paravirtualized kernel on bare hardware
[    0.504434] Time:  4:58:33  Date: 03/18/09
[    0.504473] NET: Registered protocol family 16
[    0.504507] EISA bus registered
[    0.504507] ACPI: bus type pci registered
[    0.504507] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.504507] PCI: MCFG area at e0000000 reserved in E820
[    0.504507] PCI: Using MMCONFIG for extended config space
[    0.504507] PCI: Using configuration type 1 for base access
[    0.509464] ACPI: EC: Look up EC in DSDT
[    0.526720] ACPI: Interpreter enabled
[    0.526726] ACPI: (supports S0 S1 S4 S5)
[    0.526751] ACPI: Using IOAPIC for interrupt routing
[    0.540595] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540595] PCI: 0000:00:00.0 reg 10 32bit mmio: [d8000000, dfffffff]
[    0.540672] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.540679] pci 0000:00:02.0: PME# disabled
[    0.540751] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.540757] pci 0000:00:03.0: PME# disabled
[    0.540820] PCI: 0000:00:0f.0 reg 10 io port: [fc00, fc07]
[    0.540829] PCI: 0000:00:0f.0 reg 14 io port: [f800, f803]
[    0.540838] PCI: 0000:00:0f.0 reg 18 io port: [f400, f407]
[    0.540847] PCI: 0000:00:0f.0 reg 1c io port: [f000, f003]
[    0.540856] PCI: 0000:00:0f.0 reg 20 io port: [ec00, ec0f]
[    0.540864] PCI: 0000:00:0f.0 reg 24 io port: [e800, e8ff]
[    0.540944] PCI: 0000:00:0f.1 reg 20 io port: [e400, e40f]
[    0.541038] PCI: 0000:00:10.0 reg 20 io port: [e000, e01f]
[    0.541067] pci 0000:00:10.0: supports D1
[    0.541070] pci 0000:00:10.0: supports D2
[    0.541073] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541078] pci 0000:00:10.0: PME# disabled
[    0.541134] PCI: 0000:00:10.1 reg 20 io port: [dc00, dc1f]
[    0.541163] pci 0000:00:10.1: supports D1
[    0.541166] pci 0000:00:10.1: supports D2
[    0.541168] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541174] pci 0000:00:10.1: PME# disabled
[    0.541230] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
[    0.541259] pci 0000:00:10.2: supports D1
[    0.541261] pci 0000:00:10.2: supports D2
[    0.541264] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541269] pci 0000:00:10.2: PME# disabled
[    0.541325] PCI: 0000:00:10.3 reg 20 io port: [d400, d41f]
[    0.541354] pci 0000:00:10.3: supports D1
[    0.541356] pci 0000:00:10.3: supports D2
[    0.541359] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541365] pci 0000:00:10.3: PME# disabled
[    0.541399] PCI: 0000:00:10.4 reg 10 32bit mmio: [fdfff000, fdfff0ff]
[    0.541450] pci 0000:00:10.4: supports D1
[    0.541452] pci 0000:00:10.4: supports D2
[    0.541455] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541460] pci 0000:00:10.4: PME# disabled
[    0.541660] PCI: 0000:00:12.0 reg 10 io port: [d000, d0ff]
[    0.541669] PCI: 0000:00:12.0 reg 14 32bit mmio: [fdffe000, fdffe0ff]
[    0.541715] pci 0000:00:12.0: supports D1
[    0.541718] pci 0000:00:12.0: supports D2
[    0.541720] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541726] pci 0000:00:12.0: PME# disabled
[    0.541940] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.541946] PCI: bridge 0000:00:01.0 32bit mmio: [fdc00000, fdcfffff]
[    0.541952] PCI: bridge 0000:00:01.0 32bit mmio pref: [fdb00000, fdbfffff]
[    0.542000] PCI: 0000:02:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.542015] PCI: 0000:02:00.0 reg 14 64bit mmio: [c0000000, cfffffff]
[    0.542029] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
[    0.542038] PCI: 0000:02:00.0 reg 24 io port: [bc00, bc7f]
[    0.542046] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.542119] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
[    0.542124] PCI: bridge 0000:00:02.0 32bit mmio: [f8000000, fbffffff]
[    0.542133] PCI: bridge 0000:00:02.0 64bit mmio pref: [c0000000, cfffffff]
[    0.542193] PCI: bridge 0000:00:03.0 io port: [a000, afff]
[    0.542199] PCI: bridge 0000:00:03.0 32bit mmio: [fde00000, fdefffff]
[    0.542207] PCI: bridge 0000:00:03.0 64bit mmio pref: [fdd00000, fddfffff]
[    0.542264] PCI: 0000:04:04.0 reg 10 32bit mmio: [fdaf0000, fdafffff]
[    0.544127] pci 0000:00:13.1: transparent bridge
[    0.544132] PCI: bridge 0000:00:13.1 io port: [9000, 9fff]
[    0.544138] PCI: bridge 0000:00:13.1 32bit mmio: [fda00000, fdafffff]
[    0.544146] PCI: bridge 0000:00:13.1 64bit mmio pref: [fd900000, fd9fffff]
[    0.544173] bus 00 -> node 0
[    0.544185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.544811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[    0.545025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.545238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[    0.634778] ACPI: PCI Root Bridge [PCI1] (0000:80)
[    0.634778] PCI: 0000:80:01.0 reg 10 64bit mmio: [bfffc000, bfffffff]
[    0.634778] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.634778] pci 0000:80:01.0: PME# disabled
[    0.634778] bus 80 -> node 0
[    0.634778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.636360] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.636691] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.637027] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[    0.637358] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
[    0.637648] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.637932] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.638212] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.638518] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[    0.638634] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.638634] pnp: PnP ACPI init
[    0.638634] ACPI: bus type pnp registered
[    0.648588] pnp: PnP ACPI: found 19 devices
[    0.648588] ACPI: ACPI bus type pnp unregistered
[    0.648588] PnPBIOS: Disabled by ACPI PNP
[    0.648588] PCI: Using ACPI for IRQ routing
[    0.652051] NET: Registered protocol family 8
[    0.652055] NET: Registered protocol family 20
[    0.652081] NetLabel: Initializing
[    0.652081] NetLabel:  domain hash size = 128
[    0.652081] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.652088] NetLabel:  unlabeled traffic allowed by default
[    0.652097] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[    0.652104] hpet0: 3 32-bit timers, 14318180 Hz
[    0.654504] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.654507]    actual entries 65620
[    0.654658] AppArmor: AppArmor Filesystem Enabled
[    0.654682] ACPI: RTC can wake from S4
[    0.656045] Switched to high resolution mode on CPU 0
[    0.656490] Switched to high resolution mode on CPU 1
[    0.656532] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.656537] system 00:01: ioport range 0x500-0x50f has been reserved
[    0.656547] system 00:02: iomem range 0xf0001000-0xf0001fff has been reserved
[    0.656556] system 00:03: iomem range 0xf0002000-0xf0002fff has been reserved
[    0.656566] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.656571] system 00:04: ioport range 0x800-0x805 has been reserved
[    0.656575] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.656578] system 00:04: ioport range 0x880-0x88f has been reserved
[    0.656602] system 00:0f: iomem range 0xf0000000-0xf0000fff has been reserved
[    0.656613] system 00:10: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.656623] system 00:12: iomem range 0xf0000-0xfffff could not be reserved
[    0.656628] system 00:12: iomem range 0xfe800000-0xfe8000ff has been reserved
[    0.656632] system 00:12: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.656636] system 00:12: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.656640] system 00:12: iomem range 0x0-0x9ffff could not be reserved
[    0.656644] system 00:12: iomem range 0x100000-0x7fedffff could not be reserved
[    0.656647] system 00:12: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.656651] system 00:12: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.656655] system 00:12: iomem range 0xfff80000-0xfffeffff could not be reserved
[    0.692274] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.692279] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.692287] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.692293] pci 0000:00:01.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.692305] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.692310] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.692317] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    0.692322] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.692331] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.692335] pci 0000:00:03.0:   IO window: 0xa000-0xafff
[    0.692343] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
[    0.692349] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.692359] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
[    0.692363] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
[    0.692370] pci 0000:00:13.1:   MEM window: 0xfda00000-0xfdafffff
[    0.692375] pci 0000:00:13.1:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.692394] pci 0000:00:01.0: setting latency timer to 64
[    0.692411] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.692417] pci 0000:00:02.0: setting latency timer to 64
[    0.692430] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.692437] pci 0000:00:03.0: setting latency timer to 64
[    0.692447] pci 0000:00:13.1: setting latency timer to 64
[    0.692452] bus: 00 index 0 io port: [0, ffff]
[    0.692455] bus: 00 index 1 mmio: [0, ffffffff]
[    0.692458] bus: 01 index 0 io port: [c000, cfff]
[    0.692461] bus: 01 index 1 mmio: [fdc00000, fdcfffff]
[    0.692464] bus: 01 index 2 mmio: [fdb00000, fdbfffff]
[    0.692466] bus: 01 index 3 mmio: [0, 0]
[    0.692469] bus: 02 index 0 io port: [b000, bfff]
[    0.692472] bus: 02 index 1 mmio: [f8000000, fbffffff]
[    0.692474] bus: 02 index 2 mmio: [c0000000, cfffffff]
[    0.692477] bus: 02 index 3 mmio: [0, 0]
[    0.692480] bus: 03 index 0 io port: [a000, afff]
[    0.692483] bus: 03 index 1 mmio: [fde00000, fdefffff]
[    0.692485] bus: 03 index 2 mmio: [fdd00000, fddfffff]
[    0.692488] bus: 03 index 3 mmio: [0, 0]
[    0.692491] bus: 04 index 0 io port: [9000, 9fff]
[    0.692494] bus: 04 index 1 mmio: [fda00000, fdafffff]
[    0.692507] bus: 04 index 2 mmio: [fd900000, fd9fffff]
[    0.692510] bus: 04 index 3 io port: [0, ffff]
[    0.692512] bus: 04 index 4 mmio: [0, ffffffff]
[    0.692515] bus: 80 index 0 io port: [0, ffff]
[    0.692518] bus: 80 index 1 mmio: [0, ffffffff]
[    0.692532] NET: Registered protocol family 2
[    0.704595] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.704975] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.705406] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.705691] TCP: Hash tables configured (established 131072 bind 65536)
[    0.705695] TCP reno registered
[    0.708649] NET: Registered protocol family 1
[    0.708806] checking if image is initramfs... it is
[    1.443953] Freeing initrd memory: 8503k freed
[    1.445838] audit: initializing netlink socket (disabled)
[    1.445857] type=2000 audit(1237352313.444:1): initialized
[    1.451240] highmem bounce pool size: 64 pages
[    1.451250] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.455272] VFS: Disk quotas dquot_6.5.1
[    1.455413] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.455572] msgmni has been set to 1743
[    1.455771] io scheduler noop registered
[    1.455775] io scheduler anticipatory registered
[    1.455778] io scheduler deadline registered
[    1.455795] io scheduler cfq registered (default)
[    1.455818] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.455943] pci 0000:02:00.0: Boot video device
[    1.456158] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.456211] pcieport-driver 0000:00:02.0: found MSI capability
[    1.456271] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.456347] pci_express 0000:00:02.0:pcie01: allocate port service
[    1.456434] pci_express 0000:00:02.0:pcie02: allocate port service
[    1.456519] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.456671] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.456729] pcieport-driver 0000:00:03.0: found MSI capability
[    1.456795] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.456867] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.456948] pci_express 0000:00:03.0:pcie02: allocate port service
[    1.457025] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.462602] aer 0000:00:02.0:pcie01: service driver aer loaded
[    1.467813] aer 0000:00:03.0:pcie01: service driver aer loaded
[    1.468232] isapnp: Scanning for PnP cards...
[    1.822320] isapnp: No Plug & Play device found
[    1.881518] hpet_resources: 0xfe800000 is busy
[    1.881625] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.881791] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.882852] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.886000] brd: module loaded
[    1.886118] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.886342] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.886812] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.886823] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.888208] mice: PS/2 mouse device common for all mice
[    1.888430] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.888470] rtc0: alarms up to one year, y3k, hpet irqs
[    1.888713] EISA: Probing bus 0 at eisa.0
[    1.888760] EISA: Detected 0 cards.
[    1.888764] cpuidle: using governor ladder
[    1.888767] cpuidle: using governor menu
[    1.889551] TCP cubic registered
[    1.889596] Using IPI No-Shortcut mode
[    1.889924] registered taskstats version 1
[    1.890106]   Magic number: 1:198:970
[    1.890273] rtc_cmos 00:07: setting system clock to 2009-03-18 04:58:34 UTC (1237352314)
[    1.890278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.890280] EDD information not available.
[    1.890583] Freeing unused kernel memory: 424k freed
[    1.890649] Write protecting the kernel text: 2580k
[    1.890688] Write protecting the kernel read-only data: 940k
[    1.912122] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.120137] fuse init (API version 7.9)
[    2.208046] fan PNP0C0B:00: registered as cooling_device0
[    2.208059] ACPI: Fan [FAN] (on)
[    2.240045] processor ACPI0007:00: registered as cooling_device1
[    2.244040] processor ACPI0007:01: registered as cooling_device2
[    2.264075] thermal LNXTHERM:01: registered as thermal_zone0
[    2.264696] ACPI: Thermal Zone [THRM] (56 C)
[    2.324045] device-mapper: uevent: version 1.0.3
[    2.324391] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.304415] No dock devices found.
[    3.392807] SCSI subsystem initialized
[    3.463600] usbcore: registered new interface driver usbfs
[    3.463656] usbcore: registered new interface driver hub
[    3.468579] usbcore: registered new device driver usb
[    3.580697] USB Universal Host Controller Interface driver v3.0
[    3.580838] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.580855] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.580934] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.580976] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
[    3.581230] usb usb1: configuration #1 chosen from 1 choice
[    3.581286] hub 1-0:1.0: USB hub found
[    3.581299] hub 1-0:1.0: 2 ports detected
[    3.607228] libata version 3.00 loaded.
[    3.644672] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.678324] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.678333] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    3.793060] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.793080] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.793145] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.793197] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
[    3.793429] usb usb2: configuration #1 chosen from 1 choice
[    3.793493] hub 2-0:1.0: USB hub found
[    3.793508] hub 2-0:1.0: 2 ports detected
[    3.904163] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    4.001010] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    4.001029] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    4.001089] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    4.001139] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    4.001360] usb usb3: configuration #1 chosen from 1 choice
[    4.001422] hub 3-0:1.0: USB hub found
[    4.001437] hub 3-0:1.0: 2 ports detected
[    4.077307] usb 1-1: configuration #1 chosen from 1 choice
[    4.080125] hub 1-1:1.0: USB hub found
[    4.082047] hub 1-1:1.0: 3 ports detected
[    4.208959] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.208977] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    4.209037] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    4.209087] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
[    4.209309] usb usb4: configuration #1 chosen from 1 choice
[    4.209389] hub 4-0:1.0: USB hub found
[    4.209409] hub 4-0:1.0: 2 ports detected
[    4.369039] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[    4.416483] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.416553] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    4.416584] pata_via 0000:00:0f.1: version 0.3.3
[    4.416748] scsi0 : pata_via
[    4.416878] scsi1 : pata_via
[    4.419901] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    4.419905] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    4.507222] usb 1-1.1: configuration #1 chosen from 1 choice
[    4.588589] ata1.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[    4.588595] ata1.00: 240121728 sectors, multi 16: LBA 
[    4.599672] ata1.01: ATA-8: WDC WD5000AAKB-00YSA0, 12.01C02, max UDMA/100
[    4.599676] ata1.01: 976773168 sectors, multi 16: LBA48 
[    4.612453] ata1.00: configured for UDMA/133
[    4.628622] ata1.01: configured for UDMA/100
[    4.800385] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
[    4.800421] ata2.01: ATAPI: CD-ROM CDU701-F, 1.0r, max MWDMA2
[    4.816268] ata2.00: configured for UDMA/33
[    4.832262] ata2.01: configured for MWDMA2
[    4.832424] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[    4.832645] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 12.0 PQ: 0 ANSI: 5
[    4.836411] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
[    4.837390] scsi 1:0:1:0: CD-ROM            SONY     CD-ROM CDU701-F  1.0r PQ: 0 ANSI: 5
[    4.837666] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    4.837688] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    4.837757] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    4.837813] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
[    4.848512] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.848718] usb usb5: configuration #1 chosen from 1 choice
[    4.848762] hub 5-0:1.0: USB hub found
[    4.848775] hub 5-0:1.0: 8 ports detected
[    4.864558] usb 1-1: USB disconnect, address 2
[    4.864562] usb 1-1.1: USB disconnect, address 3
[    5.056403] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.060779] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:7b:51:0c, IRQ 23.
[    5.061489] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    5.095277] sata_via 0000:00:0f.0: version 2.3
[    5.095302] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.095369] sata_via 0000:00:0f.0: routed to hard irq line 11
[    5.095972] scsi2 : sata_via
[    5.099201] scsi3 : sata_via
[    5.103712] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.103801] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    5.103893] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    5.103975] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    5.104979] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
[    5.104986] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
[    5.133877] Driver 'sd' needs updating - please use bus_type methods
[    5.135758] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
[    5.135804] sd 0:0:0:0: [sda] Write Protect is off
[    5.135812] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.135887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.136069] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
[    5.136103] sd 0:0:0:0: [sda] Write Protect is off
[    5.136108] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.136164] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.136173]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.155338]  sda1
[    5.155509] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.155636] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.155665] sd 0:0:1:0: [sdb] Write Protect is off
[    5.155669] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.155715] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.155811] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.155837] sd 0:0:1:0: [sdb] Write Protect is off
[    5.155841] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.155887] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.155893]  sdb: sdb1 sdb2 sdb3 sdb4
[    5.171158] sd 0:0:1:0: [sdb] Attached SCSI disk
[    5.183476] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.183486] Uniform CD-ROM driver Revision: 3.20
[    5.183649] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.186374] sr1: scsi3-mmc drive: 14x/32x cd/rw xa/form2 cdda tray
[    5.186503] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.308022] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    5.512015] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    5.600887] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    5.782265] usb 1-1: configuration #1 chosen from 1 choice
[    5.785115] hub 1-1:1.0: USB hub found
[    5.787075] hub 1-1:1.0: 3 ports detected
[    6.040532] PM: Starting manual resume from disk
[    6.040538] PM: Resume from partition 8:19
[    6.040541] PM: Checking hibernation image.
[    6.040762] PM: Resume from disk failed.
[    6.069006] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.069014] EXT3-fs: write access will be enabled during recovery.
[    6.078072] usb 1-1.1: new full speed USB device using uhci_hcd and address 5
[    6.215279] usb 1-1.1: configuration #1 chosen from 1 choice
[    7.301451] kjournald starting.  Commit interval 5 seconds
[    7.301467] EXT3-fs: sdb2: orphan cleanup on readonly fs
[    7.301477] ext3_orphan_cleanup: deleting unreferenced inode 5128767
[    7.301541] ext3_orphan_cleanup: deleting unreferenced inode 557145
[    7.301568] ext3_orphan_cleanup: deleting unreferenced inode 5128761
[    7.311756] ext3_orphan_cleanup: deleting unreferenced inode 4120637
[    7.321750] ext3_orphan_cleanup: deleting unreferenced inode 4120633
[    7.321971] ext3_orphan_cleanup: deleting unreferenced inode 4120612
[    7.321994] ext3_orphan_cleanup: deleting unreferenced inode 4120635
[    7.336344] ext3_orphan_cleanup: deleting unreferenced inode 4120579
[    7.336366] ext3_orphan_cleanup: deleting unreferenced inode 4120583
[    7.356505] ext3_orphan_cleanup: deleting unreferenced inode 2377748
[    7.371307] ext3_orphan_cleanup: deleting unreferenced inode 2377716
[    7.374260] ext3_orphan_cleanup: deleting unreferenced inode 2377750
[    7.374487] ext3_orphan_cleanup: deleting unreferenced inode 2377730
[    7.374510] ext3_orphan_cleanup: deleting unreferenced inode 2377736
[    7.374727] ext3_orphan_cleanup: deleting unreferenced inode 2375735
[    7.383455] ext3_orphan_cleanup: deleting unreferenced inode 2375714
[    7.391798] ext3_orphan_cleanup: deleting unreferenced inode 2375713
[    7.392022] ext3_orphan_cleanup: deleting unreferenced inode 2375711
[    7.406936] ext3_orphan_cleanup: deleting unreferenced inode 2375710
[    7.424730] ext3_orphan_cleanup: deleting unreferenced inode 557077
[    7.424745] EXT3-fs: sdb2: 20 orphan inodes deleted
[    7.424748] EXT3-fs: recovery complete.
[    7.454624] EXT3-fs: mounted filesystem with ordered data mode.
[   12.313393] udevd version 124 started
[   12.696331] Linux agpgart interface v0.103
[   12.736208] agpgart: Detected VIA P4M900 chipset
[   12.777282] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   13.128232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.188330] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.413855] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.428542] ACPI: Power Button (FF) [PWRF]
[   13.428708] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   13.460570] ACPI: Power Button (CM) [PWRB]
[   13.460760] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.484543] ACPI: Sleep Button (CM) [SLPB]
[   14.458475] parport_pc 00:0c: reported by Plug and Play ACPI
[   14.458532] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.392035] nvidia: module license 'NVIDIA' taints kernel.
[   15.964807] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   16.147852] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   16.147865] nvidia 0000:02:00.0: setting latency timer to 64
[   16.148159] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   16.248288] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.310955] device-mapper: multipath: version 1.0.5 loaded
[   17.011762] Bluetooth: Core ver 2.13
[   17.014939] NET: Registered protocol family 31
[   17.014945] Bluetooth: HCI device and connection manager initialized
[   17.014951] Bluetooth: HCI socket layer initialized
[   17.136739] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   17.137164] usbcore: registered new interface driver btusb
[   17.244814] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[   17.245324] ndiswrapper 0000:04:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.699446] ndiswrapper: using IRQ 17
[   17.831369] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   18.341411] wlan0: ethernet device 00:19:5b:53:bd:95 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[   18.471606] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.475990] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.476050] HDA Intel 0000:80:01.0: setting latency timer to 64
[   18.476059] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[   18.485064] usbcore: registered new interface driver ndiswrapper
[   20.204563] lp0: using parport0 (interrupt-driven).
[   20.398365] Adding 1574360k swap on /dev/sdb3.  Priority:-1 extents:1 across:1574360k
[   20.972069] EXT3 FS on sdb2, internal journal
[   23.010371] type=1505 audit(1237366735.944:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4409
[   23.214410] type=1505 audit(1237366736.148:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4414
[   23.214687] type=1505 audit(1237366736.148:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4414
[   23.386338] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.144090] ACPI: WMI: Mapper loaded
[   25.192089] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   25.249988] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   25.250002] apm: disabled - APM is not SMP safe.
[   25.381221] ppdev: user-space parallel port driver
[   25.525228] NET: Registered protocol family 10
[   25.528060] lo: Disabled Privacy Extensions
[   27.351032] Bridge firewalling registered
[   27.380523] vnet0: starting userspace STP failed, starting kernel STP
[   27.747639] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   27.749178] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   27.749189] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   27.749195] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   29.927713] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   29.927722] vboxdrv: Successfully done.
[   29.927725] vboxdrv: Found 2 processor cores.
[   29.929171] vboxdrv: fAsync=0 offMin=0x61f offMax=0x24f9
[   29.930284] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   29.930295] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   31.737347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.044190] Bluetooth: L2CAP ver 2.11
[   33.044197] Bluetooth: L2CAP socket layer initialized
[   33.066655] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.066664] Bluetooth: BNEP filters: protocol multicast
[   33.083249] Bluetooth: SCO (Voice Link) ver 0.6
[   33.083256] Bluetooth: SCO socket layer initialized
[   33.215284] Bluetooth: RFCOMM socket layer initialized
[   33.217303] Bluetooth: RFCOMM TTY layer initialized
[   33.217315] Bluetooth: RFCOMM ver 1.10
[   35.210665] eth0: link down
[   35.211182] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.444011] vnet0: no IPv6 routers present
[   37.547071] NET: Registered protocol family 17
[   37.678416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.411737] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   41.090809] hda-intel: Invalid position buffer, using LPIB read method instead.
[   41.090854] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   49.292024] wlan0: no IPv6 routers present
[  140.328579] ppdev0: registered pardevice
[  140.376546] ppdev0: unregistered pardevice
[  141.690475] Too big adjustment 32
[  141.736100] Too big adjustment 32
[  141.953068] ppdev0: registered pardevice
[  142.001007] ppdev0: unregistered pardevice
[  144.168643] ppdev0: registered pardevice
[  144.216689] ppdev0: unregistered pardevice
```

Any ideas?

P.S. Please no "do a fresh install" suggestion. I moved from Windows largely because of that. Reformatting doesn't solve anything.

---

### Post by e_james on 2009-03-18
I can't help with the technalities of linux, but your symptoms could be the consequences of a hardware fault. Possible candidates include fauly RAM, overheating CPU or chipset or PSU. One of my machines would reboot randomly, but commonly after starting the dvd drive - a replacement PSU fixed that. Another PC freezes completely (no mouse movement, no keyboard) when the room temperature reaches about 30 degrees C. I'm pretty sure it's not the CPU because the reported temp. is quite comfortable; I suspect the chip set.

---

### Post by LowSky on 2009-03-18
Could you please give us your hard ware specs ad please post the results of this command  
thanks
```
lspc -v
```


I think you have a hardware issue, most likely a bad motherboard. the exact issue being the North Bridge Chip overheating is my first guess. this chip can handle many things like: graphics, system bus, drive communication, and usb ports. If it goes bad freeze ups and drops can occur

[B]
EDIT: I just read your other thread and it seems to be a Kernel/BIOS issue like before, I havent read your logs but I suspect that issue is still the problem.

But calling a motherboard issue is basically what it boils down to, you have a motherboard that was poorly designed and it fails to run the OS correctly, I'm only saying that because you mentioned that Windows did the same things, which makes me want to blame the Motherboard designer and not the Software[/B]

---

### Post by mahasmb on 2009-03-18
Thank you very much for your replies.

I used to have quite a few Windows problems yes (2 years ago or so). But since then and since moving to Ubuntu I've switched out every part of my computer except the PSU, processor and the optical drives. Everything else is completely new (RAM, motherboard, HDD, graphics card, wireless card as of nearly a year ago.

My motherboard is a Biostar P4M900-M4, socket 478, Micro ATX motherboard for an Intel processor. It's even certified for Vista... it should really be able to run Ubuntu well as far as I can tell.

Just in case:
$lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
04:04.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

$lsusb
```
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0a5c:2100 Broadcom Corp. Bluetooth 2.0+eDR dongle
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Therion on 2009-03-18
I'm going to risk my head being ripped off and suggest you try installing 8.04 (Hardy Heron).  Sometimes one particular disro release simply isn't your PC's proverbial cup of tea.  
Intrepid wasn't mine either (I had no END of weirdness using it) while both Hardy and even Jaunty (still in Alpha!) run like mad-champs on my system.

---

### Post by Kevbert on 2009-03-18
Please run memtest for a couple of passes from the grub boot menu. You should get no errors.

---

### Post by e_james on 2009-03-19
mahasmb

Unfortunately just because hardware is new it doesn't mean it's not faulty. A friend of mine used to build PCs and he had plenty of problems with hardware fresh from the supplier. I also notice that you said you didn't change the PSU but you did change the graphics card. I would expect a new graphics card to draw more power and this could stress an older PSU. 

If it was my PC, after running the memory test (with satisfactory results), I would try prolonged operation with a variety of Live CDs, old and new. If they all show the same undesirable behaviour, it would seem that the hardware is faulty or it really doesn't like linux. If some of them work well, then the problem should have a software fix. Possible live CDs include Damn Small Linux, Puppy, Gparted and Knoppix.

---

### Post by mahasmb on 2009-03-20
Thank you everyone for all your help.

I've gone through some power supply calculators and it seems I may be coming in short on that... so I'll be getting myself a new PSU.

When I go to bed tonight, I'll run that memtest and leaving it running until I get back from work tomorrow.

I'll also try running a LiveCD, which I think is an awesome testing procedure, from your explanation. I wish I had thought of it.

I'll post my results in the next few days as I get them.

Once again, thanks a bunch. You're suggestions are actually giving me something to work with. You've been a great help!

_**Edit as of Sunday, March 22nd**_: 
- I've run memtest and everything passed. No errors! 
- I've also downgraded my Video Card to one that uses a PCI slot instead of a PCI-Express slot (I understand this should reduce the power consumption. I can't really afford a new PSU right now, so I just switched my newer card with my brother's older/weaker card).
- I will try the LiveCD next.
- Also, I think my wireless problems may be due a faulty wireless card (of course wireless is only one of my many problems) so I'm using an old wireless card I have around for testing purposes to see if it decides to also stop working randomly.

---

### Post by mahasmb on 2009-04-06
It's definitely hardware... I'm gonna spend some money I don't have to have it checked out. It's getting in the way of getting my school work done.

---

### Post by phantom3113 on 2009-04-06
I have no help to offer, but I would like to offer emotional support :D I feel immensely bad for your mountain of issues. Hope they get resolved soon!

---

