---
title: "Ipod Mount problems"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Jeeevs2001 on 2006-01-11
Very new to all this and having a few problems! Having sorted out the difficulties with mounting a second hard disk and loading the software (MultiSync) to sync my PPC another issue has come up. My ipod will no longer mount. First it would say that the drive was unmountable so (using my old windows laptop) i reinstalled the ipod software (this solved the problem last time). Unfortunatly now when i plug in the ipod it does not even register that it is pluged in. 

Prior to this it was mounting fine and i was able to use gtkpod to put music on. Any help would be great!

---

### Post by shanghaipi on 2006-01-11
Open the terminal and type:
```
sudo fdisk -l
```
This will hopefully show whether Ubuntu is even recognizing that you have ipod plugged into the computer.  From there, hopefully we can help you out.  Paste your results.

---

### Post by Jeeevs2001 on 2006-01-12
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4912    39455608+  83  Linux
/dev/hda2            4913        5005      747022+   5  Extended
/dev/hda5            4913        5005      746991   82  Linux swap / Solaris

Disk /dev/hdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15017   120624021   83  Linux


This is the output. It does not look to me as if it is even registered.  The ipod is plugged in through a firewire port rather than USB, if that makes any difference. However it did work through firewire before.

---

### Post by Jeeevs2001 on 2006-01-15
interestingly my 'dmesg' output is totaly messed up to: 

ule license 'NVIDIA' taints kernel.
[4294695.385000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294695.386000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294695.623000] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[4294696.214000] ts: Compaq touchscreen protocol output
[4294699.330000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294700.286000] cdrom: open failed.
[4294700.293000] cdrom: open failed.
[4294700.969000] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[4294702.759000] agpgart: Detected VIA PM266/KM266 chipset
[4294702.790000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294702.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.979000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294702.979000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294703.170000] ieee1394: Initialized config rom entry `ip1394'
[4294703.188000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294703.188000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294703.199000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294703.251000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[de021000-de0217ff]  Max Packet=[2048]
[4294703.423000] adm8211: Copyright 2003, Jouni Malinen <jkmaline@cc.hut.fi>; Copyright 2004-2005, Michael Wu <flamingice@sourmilk.net>
[4294703.423000] adm8211: release 20050620
[4294703.432000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294703.557000] 0000:00:07.0 (adm8211): EEPROM type 93C46
[4294703.560000] 0000:00:07.0 (adm8211): Channel range: 1 - 13
[4294703.560000] 0000:00:07.0 (adm8211): RFtype=1 BBPtype=1 Specific BBP=0 Transceiver=0
[4294703.568000] eth1: hwaddr 00:30:bd:e1:08:c7, IRQ 18, Rev 0x11
[4294704.273000] irda_init()
[4294704.273000] NET: Registered protocol family 23
[4294704.522000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c010000009e][4294705.124000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294705.124000]          Please try dxs_support=5 option
[4294705.124000]          and report if it works on your machine.
[4294705.124000]          For more details, read ALSA-Configuration.txt.
[4294705.125000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[4294705.125000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[4294705.125000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[4294705.125000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 6
[4294705.125000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294708.410000] Real Time Clock Driver v1.12
[4294708.531000] input: PC Speaker
[4294708.803000] FDC 0 is a post-1991 82077
[4294711.512000] eth1: scanning..
[4294711.739000] NET: Registered protocol family 17
[4294713.580000] eth1: CHAN=11 BSSID=00:30:54:40:54:2e SSID=SWAMR-54108 RSSI=0 num=1/2 score=0
[4294713.580000] eth1: new BSSID 00:30:54:40:54:2e
[4294713.645000] eth1: authenticate with AP 00:30:54:40:54:2e CHAN=11
[4294713.645000] eth1: TX authentication (alg=1 transaction=1)
[4294713.657000] eth1: RX authentication (alg=1 transaction=2 status=13 Authentication algorithm not supported)
[4294713.657000] eth1: Falling back on open authentication...
[4294714.710000] eth1: authenticate with AP 00:30:54:40:54:2e CHAN=11
[4294714.710000] eth1: TX authentication (alg=0 transaction=1)
[4294714.723000] eth1: RX authentication (alg=0 transaction=2 status=0 Success)
[4294714.723000] eth1: authenticated
[4294714.723000] eth1: associate with AP 00:30:54:40:54:2e
[4294714.723000] eth1: TX AssocReq (capab=0x471)
[4294714.724000] eth1: RX AssocResp (capab=0x471 aid=2 status=0 Success)
[4294714.724000] eth1: associated
[4294715.042000] eth1: LinkOn
[4294717.490000] NET: Registered protocol family 10
[4294717.490000] Disabled Privacy Extensions on device c02eb280(lo)
[4294717.530000] IPv6 over IPv4 tunneling driver
[4294719.057000] ACPI: Power Button (FF) [PWRF]
[4294719.057000] ACPI: Power Button (CM) [PWRB]
[4294719.057000] ACPI: Sleep Button (CM) [SLPB]
[4294719.254000] ibm_acpi: ec object not found
[4294726.651000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294726.651000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294726.651000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294726.855000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294726.855000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294726.855000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294727.745000] eth1: no IPv6 routers present
[4294730.421000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294730.421000] apm: overridden by ACPI.
[4294731.617000] ip_tables: (C) 2000-2002 Netfilter core team
[4294731.902000] ip_conntrack version 2.1 (2047 buckets, 16376 max) - 248 bytes per conntrack
[4294733.423000] Bluetooth: Core ver 2.7
[4294733.423000] NET: Registered protocol family 31
[4294733.423000] Bluetooth: HCI device and connection manager initialized
[4294733.423000] Bluetooth: HCI socket layer initialized
[4294733.450000] Bluetooth: L2CAP ver 2.7
[4294733.450000] Bluetooth: L2CAP socket layer initialized
[4294733.483000] Bluetooth: RFCOMM ver 1.5
[4294733.483000] Bluetooth: RFCOMM socket layer initialized
[4294733.484000] Bluetooth: RFCOMM TTY layer initialized
[4295127.613000] Inbound IN=eth1 OUT= MAC=00:30:bd:e1:08:c7:00:30:54:40:54:2c:08:00 SRC=66.35.250.209 DST=192.168.1.4 LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=56834 DF PROTO=TCP SPT=80 DPT=35549 WINDOW=5840 RES=0x00 ACK URGP=0
[4295135.931000] Inbound IN=eth1 OUT= MAC=00:30:bd:e1:08:c7:00:30:54:40:54:2c:08:00 SRC=213.228.0.141 DST=192.168.1.4 LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=33388 DF PROTO=TCP SPT=5319 DPT=48240 WINDOW=5840 RES=0x00 ACK URGP=0
[4295781.007000] eth1: LinkOff
[4295781.107000] eth1: scanning..
[4295783.174000] eth1: CHAN=11 BSSID=00:30:54:40:54:2e SSID=SWAMR-54108 RSSI=17 num=5194/2 score=17
[4295785.535000] eth1: LinkOn
[4295908.987000] eth1: LinkOff
[4295909.087000] eth1: scanning..
[4295911.154000] eth1: CHAN=11 BSSID=00:30:54:40:54:2e SSID=SWAMR-54108 RSSI=12 num=5790/3 score=12
[4295911.302000] eth1: LinkOn
[4295964.034000] ibm_acpi: ec object not found
[4296493.854000] eth1: LinkOff
[4296493.954000] eth1: scanning..
[4296496.021000] eth1: CHAN=11 BSSID=00:30:54:40:54:2e SSID=SWAMR-54108 RSSI=9 num=8595/3 score=9
[4296502.962000] eth1: LinkOn
[4296519.466000] eth1: RX deauthentication from 00:30:54:40:54:2e (reason=7)
[4296519.532000] eth1: authenticate with AP 00:30:54:40:54:2e CHAN=11
[4296519.532000] eth1: TX authentication (alg=0 transaction=1)
[4296519.544000] eth1: RX authentication (alg=0 transaction=2 status=0 Success)
[4296519.544000] eth1: authenticated
[4296519.544000] eth1: associate with AP 00:30:54:40:54:2e
[4296519.544000] eth1: TX AssocReq (capab=0x471)
[4296519.546000] eth1: RX AssocResp (capab=0x471 aid=1 status=0 Success)
[4296519.546000] eth1: associated
[4296705.461000] atkbd.c: Unknown key released (translated set 2, code 0x0 on isa0060/serio0).
[4296705.461000] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
[4296705.516000] atkbd.c: Unknown key released (translated set 2, code 0x0 on isa0060/serio0).
[4296705.516000] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
[4296705.568000] atkbd.c: Unknown key released (translated set 2, code 0x0 on isa0060/serio0).
[4296705.568000] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
[4296705.594000] atkbd.c: Unknown key released (translated set 2, code 0x0 on isa0060/serio0).
[4296705.594000] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
[4296787.343000] usb 4-4: new high speed USB device using ehci_hcd and address 2[4296788.175000] SCSI subsystem initialized
[4296788.188000] Initializing USB Mass Storage driver...
[4296788.191000] scsi0 : SCSI emulation for USB Mass Storage devices
[4296788.197000] usb-storage: device found at 2
[4296788.197000] usb-storage: waiting for device to settle before scanning
[4296788.197000] usbcore: registered new driver usb-storage
[4296788.197000] USB Mass Storage support registered.
[4296793.197000]   Vendor:           Model: disgo             Rev: 1.04
[4296793.197000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296793.249000] usb-storage: device scan complete
[4296794.155000] SCSI device sda: 2004992 512-byte hdwr sectors (1027 MB)
[4296794.156000] sda: Write Protect is off
[4296794.156000] sda: Mode Sense: 23 00 00 00
[4296794.156000] sda: assuming drive cache: write through
[4296794.162000] SCSI device sda: 2004992 512-byte hdwr sectors (1027 MB)
[4296794.163000] sda: Write Protect is off
[4296794.163000] sda: Mode Sense: 23 00 00 00
[4296794.163000] sda: assuming drive cache: write through
[4296794.163000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4296794.167000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4296806.669000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4296928.628000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296928.628000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296928.746000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296928.746000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.229000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296929.229000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.373000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296929.373000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.464000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296929.464000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.564000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296929.564000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.637000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296929.637000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.744000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296929.744000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.805000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296929.805000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296929.927000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296929.927000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296931.295000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296931.295000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296931.401000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296931.401000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296936.540000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296936.540000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296936.658000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296936.658000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296968.515000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296968.515000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296968.682000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296968.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296968.798000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296968.798000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296969.608000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296969.608000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296969.877000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296969.877000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296970.049000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296970.049000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296970.078000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296970.078000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296970.911000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296970.911000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296971.294000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296971.294000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296973.209000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296973.209000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296973.483000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296973.483000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296973.639000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296973.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296973.722000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296973.722000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296973.852000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296973.852000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296974.411000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296974.411000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296974.539000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296974.539000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.054000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296975.054000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.188000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296975.188000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.282000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296975.282000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.426000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296975.426000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.509000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296975.509000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296975.631000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296975.631000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297257.486000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297257.486000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297257.599000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297257.599000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

Does anyone know what that error is? I think this may have something to do with the Ipod problem. Also myUSB wont mount automacticaly i have to do it manualy through 'System > Administration > Disks', even though it shows up in 'Computer' as unmountable. 

Can anyone help? I am (obviosly) new to this so will supply any additional info which is needed! 

Thanks in advance

---

### Post by astoltz on 2006-01-15
If you're referring to the "atkbd.c: Unknown key pressed..." errors, no, they don't have anything to do with the ipod.  They are caused by the "hotkey-setup" service which tries to bind special keys useful for laptops.  I don't know all the details but disabling this service stops the error messages.

you can have a look at [this]("http://ubuntuforums.org/archive/index.php/t-76271.html") thread for more info.

---

### Post by Jeeevs2001 on 2006-01-15
Thanks for this, I have followed the instructions here but this does not seem to have solved the problem. To be honest I don't mind abbout the error message for now I would just like to get the Ipod sorted so I can listen to some tunes! 

Could the Ipod mount problem be conected to the USB flash drive mount problem?

---

### Post by Jeeevs2001 on 2006-01-15
Update: 

There is now an ipod icon under 'Computer' but it is not the same icon which appeared before. Also when I try to mount it I get an error message 'given UDI is not a mountable volume'. When i try to mount it manualy (through 'Disks' under administration) all works well but it is read only so i can't update it with any new songs! 

Any help would be fab!

---

### Post by astoltz on 2006-01-15
It seems you are not alone with this problem.  I did a little searching and there are lots of topics with people trying all sorts of things.  A couple things to try that looked promising:

Add the user 'hal' to the following groups: 'cdrom floppy tape audio plugdev scanner'. You can do that by editing the file /etc/group or though the GUI (System -> Administration -> Users and Groups).

Then restart the dbus service: ```
sudo /etc/init.d/dbus restart
```

---

### Post by Jeeevs2001 on 2006-01-17
Success, or at least partial success. Though the ipod would not mount when I plugged it in I re-started the comp. with the ipod still attached and it has mounted fine. I am just uploading songs to it now! Though this is not an ideal solution I will have to wait and see how it works from here. Will keep you updated. Thanks for all your help / suggestions!

---

