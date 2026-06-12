---
title: "Dell E6410 Webcam not detected"
date: 2010-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iman00b on 2010-10-30
I installed Ubuntu 10.4 64 bit on my Dell Latitude E6410 and am having issue with my webcam. It is not showing up in lsusb and there are no errors in dmesg.

Here are the outputs of both.

```
Bus 002 Device 004: ID 0a5c:5801 Broadcom Corp. 
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

[    0.855234] usbcore: registered new interface driver usbfs
[    0.855242] usbcore: registered new interface driver hub
[    0.855262] usbcore: registered new device driver usb
[    0.972433] usb usb1: configuration #1 chosen from 1 choice
[    0.992344] usb usb2: configuration #1 chosen from 1 choice
[    1.293333] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.443491] usb 1-1: configuration #1 chosen from 1 choice
[    1.571661] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.722087] usb 2-1: configuration #1 chosen from 1 choice
[    2.002405] usb 2-1.7: new full speed USB device using ehci_hcd and address 3
[    2.115591] usb 2-1.7: configuration #1 chosen from 1 choice
[    2.192094] usb 2-1.8: new full speed USB device using ehci_hcd and address 4
[    2.337505] usb 2-1.8: configuration #0 chosen from 1 choice
[    2.337508] usb 2-1.8: config 0 descriptor??
[   15.621172] usbcore: registered new interface driver btusb
[ 1916.130666] usb 2-1.2: new high speed USB device using ehci_hcd and address 5
[ 1916.241487] usb 2-1.2: configuration #1 chosen from 1 choice
[ 1916.331784] usb-storage: device found at 5
[ 1916.331788] usb-storage: waiting for device to settle before scanning
[ 1916.331815] usbcore: registered new interface driver usb-storage
[ 1921.326275] usb-storage: device scan complete
[ 3668.261189] usb 2-1.2: USB disconnect, address 5
[ 3678.163039] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage xt_tcpudp aesni_intel cryptd aes_x86_64 aes_generic iptable_filter ip_tables x_tables vmnet vmblock vmci vmmon rfcomm sco bridge stp bnep l2cap binfmt_misc snd_hda_codec_intelhdmi snd_hda_codec_idt fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event snd_seq snd_timer snd_seq_device snd iwlagn soundcore iwlcore i915 sdhci_pci snd_page_alloc drm_kms_helper sdhci mac80211 ppdev drm psmouse btusb cfg80211 serio_raw i2c_algo_bit led_class intel_agp bluetooth parport_pc video dell_wmi output lp dcdbas parport e1000e ohci1394 ahci ieee1394
[ 3679.694688] btusb_intr_complete: hci0 urb ffff880202b03600 failed to resubmit (1)
[ 3679.694893] btusb_bulk_complete: hci0 urb ffff880202b039c0 failed to resubmit (1)
[ 3679.695007] btusb_bulk_complete: hci0 urb ffff880202b03900 failed to resubmit (1)
[18446744054.741657] PM: resume of drv:usb dev:2-1 complete after 102.910 msecs
[18446744054.822222] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.933756] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.933760] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.181094] PM: resume of drv:usb dev:2-1.7 complete after 440.108 msecs
[   15.898511] usb 2-1.2: new full speed USB device using ehci_hcd and address 6
[   16.010373] usb 2-1.2: configuration #1 chosen from 1 choice
[   16.135502] usbcore: registered new interface driver usbserial
[   16.136180] usbcore: registered new interface driver usbserial_generic
[   16.136185] usbserial: USB Serial Driver core
[   16.143156] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[   16.143422] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[   16.143448] usbcore: registered new interface driver option
[ 3201.553301] btusb_intr_complete: hci0 urb ffff8801edade540 failed to resubmit (1)
[ 3201.553434] btusb_bulk_complete: hci0 urb ffff8801edade780 failed to resubmit (1)
[ 3201.553551] btusb_bulk_complete: hci0 urb ffff8801edade6c0 failed to resubmit (1)
[   15.886070] usb usb1: root hub lost power or was reset
[   15.890034] usb usb2: root hub lost power or was reset
[   16.228845] PM: restore of drv:usb dev:usb1 complete after 258.004 msecs
[   16.488366] PM: restore of drv:usb dev:usb2 complete after 259.911 msecs
[   16.608215] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   16.977710] PM: restore of drv:usb dev:2-1 complete after 481.864 msecs
[   17.057703] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[   17.169769] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[   17.169773] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[   17.417041] PM: restore of drv:usb dev:2-1.7 complete after 439.979 msecs
[   17.497079] usb 2-1.8: reset full speed USB device using ehci_hcd and address 4
[   17.615248] PM: restore of drv:usb dev:2-1.8 complete after 198.500 msecs
[   17.726597] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   17.987034] usb 2-1.2: USB disconnect, address 6
[   61.560695] btusb_intr_complete: hci0 urb ffff8801edbf9c00 failed to resubmit (1)
[   61.560891] btusb_bulk_complete: hci0 urb ffff8801edbf9000 failed to resubmit (1)
[   61.561128] btusb_bulk_complete: hci0 urb ffff8801edbf9b40 failed to resubmit (1)
[18446744054.708627] PM: resume of drv:usb dev:2-1 complete after 107.601 msecs
[18446744054.788707] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.900754] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.900758] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.148050] PM: resume of drv:usb dev:2-1.7 complete after 440.071 msecs
[  104.538360] usb 2-1.1: new full speed USB device using ehci_hcd and address 7
[  104.649866] usb 2-1.1: configuration #1 chosen from 1 choice
[  104.650461] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  104.650853] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[ 4396.427975] usb 2-1.1: USB disconnect, address 7
[ 4502.181137] btusb_intr_complete: hci0 urb ffff8801753f2600 failed to resubmit (1)
[ 4502.181302] btusb_bulk_complete: hci0 urb ffff8801753f2240 failed to resubmit (1)
[ 4502.181494] btusb_bulk_complete: hci0 urb ffff8801753f2f00 failed to resubmit (1)
[18446744054.757642] PM: resume of drv:usb dev:2-1 complete after 108.211 msecs
[18446744054.837661] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.949609] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.949613] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.197001] PM: resume of drv:usb dev:2-1.7 complete after 440.003 msecs
[ 1884.679027] btusb_intr_complete: hci0 urb ffff8801a0eaf900 failed to resubmit (1)
[ 1884.679101] btusb_bulk_complete: hci0 urb ffff8801a0eaf0c0 failed to resubmit (1)
[ 1884.679226] btusb_bulk_complete: hci0 urb ffff8801a0eaf600 failed to resubmit (1)
[18446744054.743573] PM: resume of drv:usb dev:2-1 complete after 104.369 msecs
[18446744054.823598] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.935563] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.935567] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.182978] PM: resume of drv:usb dev:2-1.7 complete after 440.053 msecs
[ 5439.727585] btusb_intr_complete: hci0 urb ffff880215dad780 failed to resubmit (1)
[ 5439.727691] btusb_bulk_complete: hci0 urb ffff880215dada80 failed to resubmit (1)
[ 5439.727922] btusb_bulk_complete: hci0 urb ffff880215dad000 failed to resubmit (1)
[18446744054.773464] PM: resume of drv:usb dev:2-1 complete after 110.469 msecs
[18446744054.853500] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.965663] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.965668] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.212843] PM: resume of drv:usb dev:2-1.7 complete after 440.027 msecs
[ 4414.786206] btusb_intr_complete: hci0 urb ffff88013754e540 failed to resubmit (1)
[ 4414.786409] btusb_bulk_complete: hci0 urb ffff88013754e300 failed to resubmit (1)
[ 4414.786699] btusb_bulk_complete: hci0 urb ffff88013754ed80 failed to resubmit (1)
[18446744054.721032] PM: resume of drv:usb dev:2-1 complete after 107.725 msecs
[18446744054.801100] usb 2-1.7: reset full speed USB device using ehci_hcd and address 3
[18446744054.913164] btusb 2-1.7:1.0: no reset_resume for driver btusb?
[18446744054.913169] btusb 2-1.7:1.1: no reset_resume for driver btusb?
[18446744055.160478] PM: resume of drv:usb dev:2-1.7 complete after 440.090 msecs
```Any suggestions?

---

