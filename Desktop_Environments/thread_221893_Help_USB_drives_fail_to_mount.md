---
title: "Help USB drives fail to mount"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Hellcom on 2006-07-24
In 5.10 I didn't have any trouble mounting a usb drive flash, mp3, or HDD. However, after doing a fresh install of Dapper 6.06 and downloading all the updates it won't mount anything. Other USB devices work fine; mouse, keyboard, printer.

Dmesg Repot

```

[17182174.748000] usb 1-4: new high speed USB device using ehci_hcd and address 4
[17182175.748000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is pro bably using the wrong IRQ.
[17182186.296000] usb 1-4: device not accepting address 4, error -110
[17182186.408000] usb 1-4: new high speed USB device using ehci_hcd and address 5
[17182197.952000] usb 1-4: device not accepting address 5, error -110
[17182198.064000] usb 1-4: new high speed USB device using ehci_hcd and address 6
[17182208.488000] usb 1-4: device not accepting address 6, error -110
[17182208.600000] usb 1-4: new high speed USB device using ehci_hcd and address 7
[17182219.028000] usb 1-4: device not accepting address 7, error -110
[17182219.352000] usb 1-4: new high speed USB device using ehci_hcd and address 8
[17182230.896000] usb 1-4: device not accepting address 8, error -110
[17182236.740000] usb 1-3: new high speed USB device using ehci_hcd and address 10
[17182248.284000] usb 1-3: device not accepting address 10, error -110
[17182473.116000] usb 1-4: new high speed USB device using ehci_hcd and address 12
[17182484.660000] usb 1-4: device not accepting address 12, error -110
[17182484.772000] usb 1-4: new high speed USB device using ehci_hcd and address 13
[17182496.316000] usb 1-4: device not accepting address 13, error -110
[17182496.804000] usb 1-4: new high speed USB device using ehci_hcd and address 15
[17182508.348000] usb 1-4: device not accepting address 15, error -110
[17182508.652000] usb 1-4: new high speed USB device using ehci_hcd and address 17
[17182520.196000] usb 1-4: device not accepting address 17, error -110
[17182520.308000] usb 1-4: new high speed USB device using ehci_hcd and address 18
[17182531.852000] usb 1-4: device not accepting address 18, error -110
[17182531.964000] usb 1-4: new high speed USB device using ehci_hcd and address 19
[17182542.388000] usb 1-4: device not accepting address 19, error -110
[17182542.500000] usb 1-4: new high speed USB device using ehci_hcd and address 
```

---

### Post by Hellcom on 2006-07-24
Bump

anyone?

---

### Post by Hellcom on 2006-07-24
Can someone please help, or point me to a place where I can get help? Please](*,)

---

### Post by Hellcom on 2006-07-24
Well it doesn't seem like anyone has an answer, but anyone else who has this problem a fresh install seems to work. Just don't apply any updates until they fix the issue.

---

### Post by endfx on 2006-07-24
Can you plug in your usb device and post the results of :
"lspci"
(without the quotes)

---

### Post by endfx on 2006-07-24
Oh, nevermind you got it working :)

---

### Post by n8bounds on 2006-07-24
> **endfx said:**
> Oh, nevermind you got it working :)


I'm having the same problem...

here is my lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 500] (rev a3)
0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)


and here is the tail from my dmesg repo

[17179616.656000] Bluetooth: RFCOMM ver 1.7
[17179985.056000] usb 4-6: new high speed USB device using ehci_hcd and address 6
[17179985.168000] usb 4-6: device descriptor read/64, error -71
[17179985.384000] usb 4-6: device descriptor read/64, error -71
[17179985.600000] usb 4-6: new high speed USB device using ehci_hcd and address 7
[17179985.712000] usb 4-6: device descriptor read/64, error -71
[17179985.928000] usb 4-6: device descriptor read/64, error -71
[17179986.144000] usb 4-6: new high speed USB device using ehci_hcd and address 8
[17179986.552000] usb 4-6: device not accepting address 8, error -71
[17179986.664000] usb 4-6: new high speed USB device using ehci_hcd and address 9
[17179987.072000] usb 4-6: device not accepting address 9, error -71
[17180002.948000] usb 4-4: new high speed USB device using ehci_hcd and address 10
[17180003.820000] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17180003.932000] usb 4-4: new high speed USB device using ehci_hcd and address 11
[17180004.804000] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17180004.916000] usb 4-4: new high speed USB device using ehci_hcd and address 12
[17180005.324000] usb 4-4: device not accepting address 12, error -71
[17180005.436000] usb 4-4: new high speed USB device using ehci_hcd and address 13
[17180005.844000] usb 4-4: device not accepting address 13, error -71
[17180063.024000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

I installed Ubuntu on this PC just two days ago, and other than ssh, qtparted and samba, I haven't installed anything on it that it didn't come with.... any hints?

---

### Post by n8bounds on 2006-07-24
ALSO... I unplugged them, did this:

$ tail -f /var/log/messages

..then plugged the drives back in...

Jul 24 21:26:26 luna gconfd (root-5072): starting (version 2.14.0), pid 5072 user 'root'
Jul 24 21:26:26 luna gconfd (root-5072): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 24 21:26:26 luna gconfd (root-5072): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 24 21:26:26 luna gconfd (root-5072): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 24 21:26:26 luna gconfd (root-5072): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 24 21:26:26 luna gconfd (root-5072): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 24 21:26:29 luna kernel: [17180063.024000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
Jul 24 21:26:56 luna gconfd (root-5072): GConf server is not in use, shutting down.
Jul 24 21:26:56 luna gconfd (root-5072): Exiting
Jul 24 21:38:51 luna -- MARK --
Jul 24 21:51:31 luna kernel: [17181565.348000] usb 4-4: new high speed USB device using ehci_hcd and address 14
Jul 24 21:51:32 luna kernel: [17181566.332000] usb 4-4: new high speed USB device using ehci_hcd and address 15
Jul 24 21:51:33 luna kernel: [17181567.316000] usb 4-4: new high speed USB device using ehci_hcd and address 16
Jul 24 21:51:34 luna kernel: [17181567.836000] usb 4-4: new high speed USB device using ehci_hcd and address 17
Jul 24 21:52:42 luna kernel: [17181635.656000] usb 4-6: new high speed USB device using ehci_hcd and address 18
Jul 24 21:52:42 luna kernel: [17181636.200000] usb 4-6: new high speed USB device using ehci_hcd and address 19
Jul 24 21:52:43 luna kernel: [17181636.744000] usb 4-6: new high speed USB device using ehci_hcd and address 20
Jul 24 21:52:43 luna kernel: [17181637.264000] usb 4-6: new high speed USB device using ehci_hcd and address 21

---

### Post by Hellcom on 2006-07-25
> **endfx said:**
> Oh, nevermind you got it working :)

Well working if I don't apply any updates... >.>

This is the Ispci report:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host B ridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChr ome] Integrated Video (rev 01)


It may be different to what you expected as the usb drives are now working.

---

### Post by endfx on 2006-07-25
I'm really sorry. I didn't mean "lspci".

I mean "lsusb"

My bad. Do "lsusb". It is MUCH easier to read than the output of "lspci"

Please post that.

---

