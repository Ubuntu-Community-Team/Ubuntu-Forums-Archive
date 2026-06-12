---
title: "Epson CX9400FAX Redetected Repeatedly"
date: 2009-05-18
forum: General Help
---

### Post by ljohnk on 2009-05-18
I am using Ubuntu 8.10, kernel 2.6.27-14-generic and have an Epson CX9400Fax printer/scanner connected by USB. The printer and scanner work fine but there is an annoying "feature" that I have been unable to fix. If I leave the printer on but unused for a period of time, say an hour, a dialog pops up saying something like New Printer Found, and a printer is added, usually with a generic text only driver. I snipped a section from my System log. Something like this repeats over and over in the log. Any ideas how to make the system let my perfectly working printer alone?

> May 18 16:11:07 localhost hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 18 16:11:07 localhost hal_lpadmin: Polling device ID from the printer
May 18 16:11:07 localhost hal_lpadmin: Written device ID into HAL database entry
May 18 16:11:07 localhost hal_lpadmin: remove
May 18 16:11:07 localhost hal_lpadmin: Found configured printer: CX9300F-CX9400Fax-DX9400F
May 18 16:11:07 localhost hal_lpadmin: Found configured printer: Stylus-CX9400Fax2
May 18 16:11:07 localhost hal_lpadmin: Running hal_lpadmin
May 18 16:11:08 localhost last message repeated 2 times
May 18 16:11:08 localhost hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 18 16:11:08 localhost hal_lpadmin: Polling device ID from the printer
May 18 16:11:08 localhost hal_lpadmin: Device 001:094: /org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if1
May 18 16:11:08 localhost hal_lpadmin: Stopping hal_lpadmin triggered by low-level USB device
May 18 16:11:09 localhost hal_lpadmin: hal_lpadmin triggered by usblp kernel module
May 18 16:11:09 localhost hal_lpadmin: Using device ID from HAL database entry
May 18 16:11:09 localhost hal_lpadmin: add
May 18 16:11:09 localhost hal_lpadmin: hal_lpadmin triggered by usblp kernel module
May 18 16:11:09 localhost hal_lpadmin: Using device ID from HAL database entry
May 18 16:11:09 localhost hal_lpadmin: URIs: ['usb://EPSON/Stylus%20CX9400Fax', 'hal:///org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if1_printer_noserial']
May 18 16:11:09 localhost hal_lpadmin: HPLIP Fax URIs: None
May 18 16:11:09 localhost hal_lpadmin: Not adding printer: Stylus-CX9400Fax already exists
May 18 16:11:09 localhost hal_lpadmin: Re-enabling printer Stylus-CX9400Fax
May 18 16:11:09 localhost hal_lpadmin: remove
May 18 16:11:09 localhost hal_lpadmin: Found configured printer: CX9300F-CX9400Fax-DX9400F
May 18 16:11:09 localhost hal_lpadmin: Found configured printer: Stylus-CX9400Fax
May 18 16:11:09 localhost hal_lpadmin: Disabled printer Stylus-CX9400Fax, as the corresponding device was unplugged or turned off
May 18 16:11:09 localhost hal_lpadmin: Found configured printer: Stylus-CX9400Fax2
May 18 16:11:09 localhost hal_lpadmin: Running hal_lpadmin
May 18 16:11:10 localhost hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 18 16:11:10 localhost hal_lpadmin: Polling device ID from the printer
May 18 16:11:10 localhost hal_lpadmin: Device 001:094: /org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if1
May 18 16:11:10 localhost hal_lpadmin: Stopping hal_lpadmin triggered by low-level USB device
May 18 16:11:10 localhost pulseaudio[6114]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if2_scsi_host
May 18 16:11:10 localhost hal_lpadmin: Running hal_lpadmin
May 18 16:11:10 localhost hal_lpadmin: Running hal_lpadmin
May 18 16:11:11 localhost hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 18 16:11:11 localhost hal_lpadmin: Polling device ID from the printer
May 18 16:11:11 localhost hal_lpadmin: Device 001:094: /org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if1
May 18 16:11:11 localhost hal_lpadmin: Stopping hal_lpadmin triggered by low-level USB device
May 18 16:11:11 localhost hal_lpadmin: hal_lpadmin triggered by usblp kernel module
May 18 16:11:11 localhost hal_lpadmin: Using device ID from HAL database entry
May 18 16:11:11 localhost hal_lpadmin: add
May 18 16:11:11 localhost hal_lpadmin: URIs: ['usb://EPSON/Stylus%20CX9400Fax', 'hal:///org/freedesktop/Hal/devices/usb_device_4b8_83a_040000000000000000_if1_printer_noserial']
May 18 16:11:11 localhost hal_lpadmin: HPLIP Fax URIs: None
May 18 16:11:11 localhost hal_lpadmin: Not adding printer: Stylus-CX9400Fax already exists
May 18 16:11:11 localhost hal_lpadmin: Re-enabling printer Stylus-CX9400Fax
May 18 16:11:12 localhost kernel: [ 3725.866563] usb-storage: device scan complete
May 18 16:11:12 localhost kernel: [ 3725.869276] scsi 46:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
May 18 16:11:12 localhost kernel: [ 3725.873427] sd 46:0:0:0: [sdd] Attached SCSI removable disk
May 18 16:11:12 localhost kernel: [ 3725.873675] sd 46:0:0:0: Attached scsi generic sg4 type 0
May 18 16:14:38 localhost kernel: [ 3931.866391] usblp0: removed

---

