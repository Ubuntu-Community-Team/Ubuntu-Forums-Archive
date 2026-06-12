---
title: "Ubuntu 10.10 looses Wireless Network on Latitude X300"
date: 2010-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by laluz on 2010-11-07
Every few minutes a freshly installed Ubuntu 10.10 looses a connection to a Zyxel DSL modem/wireless AP. The only things that helps is suspending it and reviving again. 
Where could I start looking for the problem / solution? 

```
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:04.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01) 

```

The log below does not make me any smarter.
```
poweruser@poweruser-Latitude-X300:~$ tail -f /var/log/messages
Nov  7 21:21:19 poweruser-Latitude-X300 pulseaudio[1537]: ratelimit.c: 1 events suppressed
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.328599] cfg80211: Calling CRDA to update world regulatory domain
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479331] cfg80211: World regulatory domain updated:
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479343]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479355]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479366]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479376]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479385]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:22:14 poweruser-Latitude-X300 kernel: [  209.479395]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:22:49 poweruser-Latitude-X300 pulseaudio[1537]: ratelimit.c: 1 events suppressed
Nov  7 21:37:29 poweruser-Latitude-X300 kernel: [ 1124.815412] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov  7 21:37:32 poweruser-Latitude-X300 kernel: [ 1127.608438] tg3 0000:02:05.0: wake-up capability enabled by ACPI
Nov  7 21:37:33 poweruser-Latitude-X300 kernel: [ 1128.878640] PM: Syncing filesystems ... done.
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.911541] Freezing user space processes ... (elapsed 0.01 seconds) done.
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.924091] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.940119] Suspending console(s) (use no_console_suspend to debug)
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.940802] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.941020] sd 0:0:0:0: [sda] Stopping disk
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.979798] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980091] Intel ICH 0000:00:1f.5: PCI INT B disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980217] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980242] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980267] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980292] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1128.980499] i915 0000:00:02.0: PCI INT A disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370204] PM: suspend of drv:sd dev:0:0:0:0 complete after 429.406 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370213] PM: suspend of drv:scsi dev:target0:0:0 complete after 429.320 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370221] PM: suspend of drv:scsi dev:host0 complete after 390.925 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370381] ata_piix 0000:00:1f.1: PCI INT A disabled
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370387] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 390.239 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370396] PM: suspend of drv: dev:pci0000:00 complete after 389.526 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370403] PM: suspend of devices complete after 430.017 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.370407] PM: suspend devices took 0.428 seconds
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.384216] PM: late suspend of devices complete after 13.803 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.472070] ACPI: Preparing to enter system sleep state S3
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.472347] PM: Saving platform NVS memory
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.490459] Disabling non-boot CPUs ...
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.490459] PM: Restoring platform NVS memory
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.491912] ACPI: Waking up from system sleep state S3
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.720781] yenta_cardbus 0000:02:03.0: proprietary Ricoh MMC controller disabled (via cardbus function)
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.720785] yenta_cardbus 0000:02:03.0: MMC cards are now supported by standard SDHCI controller
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.721508] PM: early resume of devices complete after 1.374 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.723500] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.723973] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.723999] usb usb2: root hub lost power or was reset
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724058] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724083] usb usb3: root hub lost power or was reset
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724115] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724139] usb usb4: root hub lost power or was reset
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724159] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.724190] usb usb1: root hub lost power or was reset
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.728101] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.728138] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.729658] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1129.729828] sd 0:0:0:0: [sda] Starting disk
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.220557] PM: resume of drv:usb dev:usb4 complete after 490.878 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.220573] PM: resume of drv:usb dev:usb2 complete after 492.366 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.220593] PM: resume of drv:hub dev:4-0:1.0 complete after 490.909 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.220599] PM: resume of drv:hub dev:2-0:1.0 complete after 491.000 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.244184] PM: resume of drv:i915 dev:0000:00:02.0 complete after 520.702 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.260056] firewire_core: skipped bus generations, destroying all nodes
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.268032] PM: resume of drv:firewire_ohci dev:0000:02:03.2 complete after 539.855 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.324030] PM: resume of drv:usb dev:usb3 complete after 594.424 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.324039] PM: resume of drv:hub dev:3-0:1.0 complete after 594.429 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.444034] PM: resume of drv:usb dev:usb1 complete after 715.836 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.444043] PM: resume of drv:hub dev:1-0:1.0 complete after 715.839 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.444051] PM: resume of drv: dev:ep_81 complete after 706.700 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.616031] usb 3-2: reset full speed USB device using uhci_hcd and address 2
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.741556] PM: resume of drv:Intel ICH dev:0000:00:1f.5 complete after 1013.424 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.760052] firewire_core: rediscovered device fw0
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.810007] btusb 3-2:1.0: no reset_resume for driver btusb?
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1130.810010] btusb 3-2:1.1: no reset_resume for driver btusb?
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.060125] PM: resume of drv:usb dev:3-2 complete after 1330.018 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.060135] PM: resume of drv:usb dev:3-2:1.0 complete after 1330.010 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.060142] PM: resume of drv:usb dev:3-2:1.1 complete after 1329.996 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.060149] PM: resume of drv:usb dev:3-2:1.2 complete after 1329.983 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.280301] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.280307] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.296489] ata1.00: configured for UDMA/100
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.320427] PM: resume of drv:sd dev:0:0:0:0 complete after 1590.653 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.320437] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1590.352 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.320444] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 871.009 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.460034] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.487 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.600033] PM: resume of drv:pcmcia_socket dev:pcmcia_socket1 complete after 139.987 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.600114] PM: resume of devices complete after 1878.556 msecs
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.600411] PM: resume devices took 1.880 seconds
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.600483] Restarting tasks ... done.
Nov  7 21:37:42 poweruser-Latitude-X300 kernel: [ 1131.600972] video LNXVIDEO:00: Restoring backlight state
Nov  7 21:37:43 poweruser-Latitude-X300 kernel: [ 1132.916075] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov  7 21:37:43 poweruser-Latitude-X300 kernel: [ 1132.996228] input: Bluetooth Laser Travel Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:46/input8
Nov  7 21:37:43 poweruser-Latitude-X300 kernel: [ 1132.997784] generic-bluetooth 0005:046D:B008.0002: input,hidraw0: BLUETOOTH HID v3.14 Mouse [Bluetooth Laser Travel Mouse] on 00:10:C6:4D:35:7B
Nov  7 21:37:43 poweruser-Latitude-X300 kernel: [ 1133.052579] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  7 21:37:43 poweruser-Latitude-X300 kernel: [ 1133.064362] tg3 0000:02:05.0: wake-up capability disabled by ACPI
Nov  7 21:37:44 poweruser-Latitude-X300 kernel: [ 1134.147236] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  7 21:37:46 poweruser-Latitude-X300 kernel: [ 1135.906541] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov  7 21:37:50 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  7 21:37:50 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: username = [poweruser]
Nov  7 21:37:50 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: /home/poweruser is already mounted
Nov  7 21:37:56 poweruser-Latitude-X300 kernel: [ 1145.741562] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.509380] cfg80211: Calling CRDA to update world regulatory domain
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517782] cfg80211: World regulatory domain updated:
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517787]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517792]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517796]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517801]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517805]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  7 21:44:09 poweruser-Latitude-X300 kernel: [ 1519.517809]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
^[[B^[[B^[[BNov  7 21:46:53 poweruser-Latitude-X300 kernel: [ 1682.701190] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov  7 21:46:54 poweruser-Latitude-X300 kernel: [ 1684.356451] tg3 0000:02:05.0: wake-up capability enabled by ACPI
Nov  7 21:46:55 poweruser-Latitude-X300 kernel: [ 1684.920135] PM: Syncing filesystems ... done.
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1684.952037] Freezing user space processes ... (elapsed 0.01 seconds) done.
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1684.968065] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1684.984114] Suspending console(s) (use no_console_suspend to debug)
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1684.984816] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024165] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024454] Intel ICH 0000:00:1f.5: PCI INT B disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024581] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024607] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024631] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024656] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.024886] i915 0000:00:02.0: PCI INT A disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.084055] sd 0:0:0:0: [sda] Stopping disk
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512730] PM: suspend of drv:sd dev:0:0:0:0 complete after 527.918 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512739] PM: suspend of drv:scsi dev:target0:0:0 complete after 527.832 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512747] PM: suspend of drv:scsi dev:host0 complete after 489.096 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512907] ata_piix 0000:00:1f.1: PCI INT A disabled
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512914] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 488.404 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512923] PM: suspend of drv: dev:pci0000:00 complete after 487.660 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512930] PM: suspend of devices complete after 528.551 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.512934] PM: suspend devices took 0.528 seconds
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.528205] PM: late suspend of devices complete after 15.265 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.616068] ACPI: Preparing to enter system sleep state S3
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.616325] PM: Saving platform NVS memory
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.634927] Disabling non-boot CPUs ...
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.634927] PM: Restoring platform NVS memory
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.636387] ACPI: Waking up from system sleep state S3
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.868776] yenta_cardbus 0000:02:03.0: proprietary Ricoh MMC controller disabled (via cardbus function)
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.868780] yenta_cardbus 0000:02:03.0: MMC cards are now supported by standard SDHCI controller
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.869499] PM: early resume of devices complete after 1.368 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.871486] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.871974] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872000] usb usb2: root hub lost power or was reset
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872057] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872082] usb usb3: root hub lost power or was reset
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872114] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872138] usb usb4: root hub lost power or was reset
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872157] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.872189] usb usb1: root hub lost power or was reset
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.876082] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.876119] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.877958] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1685.878014] sd 0:0:0:0: [sda] Starting disk
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.368439] PM: resume of drv:usb dev:usb4 complete after 490.460 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.368454] PM: resume of drv:usb dev:usb2 complete after 492.267 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.368543] PM: resume of drv:hub dev:4-0:1.0 complete after 490.560 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.368550] PM: resume of drv:hub dev:2-0:1.0 complete after 490.613 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.368892] PM: resume of drv:ac dev:ACPI0003:00 complete after 491.369 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.392183] PM: resume of drv:i915 dev:0000:00:02.0 complete after 520.715 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.408054] firewire_core: skipped bus generations, destroying all nodes
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.416027] PM: resume of drv:firewire_ohci dev:0000:02:03.2 complete after 539.869 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.472028] PM: resume of drv:usb dev:usb3 complete after 594.086 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.472037] PM: resume of drv:hub dev:3-0:1.0 complete after 594.090 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.592031] PM: resume of drv:usb dev:usb1 complete after 715.853 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.592040] PM: resume of drv:hub dev:1-0:1.0 complete after 715.856 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.592065] PM: resume of drv: dev:ep_81 complete after 215.773 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.704035] usb 3-2: reset full speed USB device using uhci_hcd and address 2
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.889571] PM: resume of drv:Intel ICH dev:0000:00:1f.5 complete after 1013.458 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.897658] btusb 3-2:1.0: no reset_resume for driver btusb?
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.897662] btusb 3-2:1.1: no reset_resume for driver btusb?
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1686.908056] firewire_core: rediscovered device fw0
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.148123] PM: resume of drv:usb dev:3-2 complete after 1270.042 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.148135] PM: resume of drv:usb dev:3-2:1.0 complete after 1270.034 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.148142] PM: resume of drv:usb dev:3-2:1.1 complete after 1270.022 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.148148] PM: resume of drv:usb dev:3-2:1.2 complete after 1270.010 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.652301] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.652307] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.668485] ata1.00: configured for UDMA/100
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.693002] PM: resume of drv:sd dev:0:0:0:0 complete after 1814.988 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.693012] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1814.949 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.693019] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1095.737 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.832034] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 138.912 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.972034] PM: resume of drv:pcmcia_socket dev:pcmcia_socket1 complete after 139.989 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.972118] PM: resume of devices complete after 2102.570 msecs
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.972422] PM: resume devices took 2.104 seconds
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.972495] Restarting tasks ... done.
Nov  7 21:47:10 poweruser-Latitude-X300 kernel: [ 1687.972987] video LNXVIDEO:00: Restoring backlight state
Nov  7 21:47:11 poweruser-Latitude-X300 kernel: [ 1689.020063] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov  7 21:47:11 poweruser-Latitude-X300 kernel: [ 1689.112545] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  7 21:47:12 poweruser-Latitude-X300 kernel: [ 1689.125075] tg3 0000:02:05.0: wake-up capability disabled by ACPI
Nov  7 21:47:12 poweruser-Latitude-X300 kernel: [ 1689.868428] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  7 21:47:14 poweruser-Latitude-X300 kernel: [ 1691.522498] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov  7 21:47:19 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  7 21:47:19 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: username = [poweruser]
Nov  7 21:47:19 poweruser-Latitude-X300 gnome-screensaver-dialog: pam_sm_authenticate: /home/poweruser is already mounted
Nov  7 21:47:24 poweruser-Latitude-X300 kernel: [ 1701.230480] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  7 21:47:39 poweruser-Latitude-X300 kernel: [ 1716.267781] input: Bluetooth Laser Travel Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:46/input9
Nov  7 21:47:39 poweruser-Latitude-X300 kernel: [ 1716.268516] generic-bluetooth 0005:046D:B008.0003: input,hidraw0: BLUETOOTH HID v3.14 Mouse [Bluetooth Laser Travel Mouse] on 00:10:C6:4D:35:7B


```

---

### Post by laluz on 2010-11-10
The solution was to remove gnome network applet and install wicd.

---

