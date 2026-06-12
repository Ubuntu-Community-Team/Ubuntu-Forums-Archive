---
title: "usb 3G in debian 8.2"
date: 2015-10-10
forum: Debian
---

### Post by azertyh on 2015-10-10
hello,

i installed debian 8.2 xfce on a laptop and i cant use my usb 3G on it. the same usb works perfectly on ubuntu. i think debian detects the usb as storage device, so i installed usb-modeswitch, but i cant still use it.

what did ubuntu do to detect it as 3G instead of storage device?

the syslog from ubuntu (it's still ubuntu 14.10) :
```
Oct 10 21:31:37 Vostro-1015 kernel: [   75.532068] usb usb2-port2: connect-debounce failed
Oct 10 21:31:53 Vostro-1015 kernel: [   91.556380] usb 2-2: new high-speed USB device number 4 using ehci-pci
Oct 10 21:31:53 Vostro-1015 kernel: [   91.691657] usb 2-2: New USB device found, idVendor=19d2, idProduct=1233
Oct 10 21:31:53 Vostro-1015 kernel: [   91.691665] usb 2-2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Oct 10 21:31:53 Vostro-1015 kernel: [   91.691671] usb 2-2: Product: ZTE WCDMA Technologies MSM
Oct 10 21:31:53 Vostro-1015 kernel: [   91.691675] usb 2-2: Manufacturer: ZTE,Incorporated
Oct 10 21:31:53 Vostro-1015 kernel: [   91.691679] usb 2-2: SerialNumber: MF667ZTED0010000
Oct 10 21:31:53 Vostro-1015 mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2"
Oct 10 21:31:53 Vostro-1015 mtp-probe: bus: 2, device: 4 was not an MTP device
Oct 10 21:31:53 Vostro-1015 kernel: [   91.789642] usb-storage 2-2:1.0: USB Mass Storage device detected
Oct 10 21:31:53 Vostro-1015 kernel: [   91.791286] scsi6 : usb-storage 2-2:1.0
Oct 10 21:31:53 Vostro-1015 kernel: [   91.791423] usbcore: registered new interface driver usb-storage
Oct 10 21:31:53 Vostro-1015 kernel: [   91.816240] usbcore: registered new interface driver uas
Oct 10 21:31:54 Vostro-1015 kernel: [   92.789678] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Oct 10 21:31:54 Vostro-1015 kernel: [   92.790293] scsi 6:0:0:1: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Oct 10 21:31:54 Vostro-1015 kernel: [   92.794652] sr1: scsi-1 drive
Oct 10 21:31:54 Vostro-1015 kernel: [   92.795708] sr 6:0:0:0: Attached scsi CD-ROM sr1
Oct 10 21:31:54 Vostro-1015 kernel: [   92.798279] sr 6:0:0:0: Attached scsi generic sg2 type 5
Oct 10 21:31:54 Vostro-1015 kernel: [   92.799777] sd 6:0:0:1: Attached scsi generic sg3 type 0
Oct 10 21:31:54 Vostro-1015 kernel: [   92.807312] sd 6:0:0:1: [sdb] Attached SCSI removable disk
Oct 10 21:31:54 Vostro-1015 usb_modeswitch: switch device 19d2:1233 on 002/004
Oct 10 21:31:55 Vostro-1015 usb_modeswitch[2634]: usb_modeswitch: switched to 19d2:1233 on 2/4
Oct 10 21:31:55 Vostro-1015 kernel: [   94.337237] usb 2-2: USB disconnect, device number 4
Oct 10 21:31:56 Vostro-1015 kernel: [   95.089239] usbcore: registered new interface driver usbserial
Oct 10 21:31:56 Vostro-1015 kernel: [   95.089278] usbcore: registered new interface driver usbserial_generic
Oct 10 21:31:56 Vostro-1015 kernel: [   95.089312] usbserial: USB Serial support registered for generic
Oct 10 21:31:56 Vostro-1015 kernel: [   95.127957] usbcore: registered new interface driver option
Oct 10 21:31:56 Vostro-1015 kernel: [   95.128001] usbserial: USB Serial support registered for GSM modem (1-port)
Oct 10 21:31:56 Vostro-1015 usb_modeswitch[2634]: usb_modeswitch: add device ID 19d2:1233 to driver option
Oct 10 21:31:56 Vostro-1015 usb_modeswitch[2634]: usb_modeswitch: please report the device ID to the Linux USB developers!
Oct 10 21:31:59 Vostro-1015 kernel: [   98.028092] usb 2-2: new high-speed USB device number 5 using ehci-pci
Oct 10 21:31:59 Vostro-1015 kernel: [   98.163274] usb 2-2: New USB device found, idVendor=19d2, idProduct=1270
Oct 10 21:31:59 Vostro-1015 kernel: [   98.163279] usb 2-2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Oct 10 21:31:59 Vostro-1015 kernel: [   98.163282] usb 2-2: Product: ZTE WCDMA Technologies MSM
Oct 10 21:31:59 Vostro-1015 kernel: [   98.163285] usb 2-2: Manufacturer: ZTE,Incorporated
Oct 10 21:31:59 Vostro-1015 kernel: [   98.163287] usb 2-2: SerialNumber: MF667ZTED0010000
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167383] option 2-2:1.0: GSM modem (1-port) converter detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167525] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167658] option 2-2:1.1: GSM modem (1-port) converter detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167765] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167891] option 2-2:1.2: GSM modem (1-port) converter detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.167993] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
Oct 10 21:31:59 Vostro-1015 kernel: [   98.168139] option 2-2:1.3: GSM modem (1-port) converter detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.168398] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
Oct 10 21:31:59 Vostro-1015 kernel: [   98.168530] option 2-2:1.4: GSM modem (1-port) converter detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.168633] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
Oct 10 21:31:59 Vostro-1015 kernel: [   98.168900] usb-storage 2-2:1.6: USB Mass Storage device detected
Oct 10 21:31:59 Vostro-1015 kernel: [   98.169210] scsi7 : usb-storage 2-2:1.6
Oct 10 21:31:59 Vostro-1015 mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2"
Oct 10 21:31:59 Vostro-1015 mtp-probe: bus: 2, device: 5 was not an MTP device
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB3): port attributes not fully set
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB4): port attributes not fully set
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB2): port attributes not fully set
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB1): port attributes not fully set
Oct 10 21:31:59 Vostro-1015 kernel: [   98.299914] usbcore: registered new interface driver cdc_wdm
Oct 10 21:31:59 Vostro-1015 kernel: [   98.324383] qmi_wwan 2-2:1.5: cdc-wdm0: USB WDM device
Oct 10 21:31:59 Vostro-1015 kernel: [   98.324719] qmi_wwan 2-2:1.5 wwan0: register 'qmi_wwan' at usb-0000:00:1d.7-2, WWAN/QMI device, d2:02:82:be:b6:68
Oct 10 21:31:59 Vostro-1015 kernel: [   98.324988] usbcore: registered new interface driver qmi_wwan
Oct 10 21:31:59 Vostro-1015 NetworkManager[803]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.5/net/wwan0, iface: wwan0)
Oct 10 21:31:59 Vostro-1015 NetworkManager[803]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.5/net/wwan0, iface: wwan0): no ifupdown configuration found.
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Opening device with flags 'version-info, proxy'...
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: cannot connect to proxy: Could not connect: Connection refused
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: spawning new qmi-proxy (try 1)...
Oct 10 21:31:59 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Checking version info (10 retries)...
Oct 10 21:32:00 Vostro-1015 kernel: [   99.169427] scsi 7:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Oct 10 21:32:00 Vostro-1015 kernel: [   99.173850] sd 7:0:0:0: Attached scsi generic sg2 type 0
Oct 10 21:32:00 Vostro-1015 kernel: [   99.176330] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB0): port attributes not fully set
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] QMI Device supports 5 services:
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    ctl (1.3)
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    wds (1.5)
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    dms (1.2)
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    nas (1.0)
Oct 10 21:32:01 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    auth (1.0)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <info>  Creating modem with plugin 'ZTE' and '7' ports
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  Could not grab port (tty/ttyUSB3): 'Cannot add port 'tty/ttyUSB3', unhandled serial type'
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <info>  Modem for device at '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2' successfully created
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Opening device with flags 'version-info, net-802-3, net-no-qos-header, proxy'...
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Checking version info (10 retries)...
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] QMI Device supports 5 services:
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    ctl (1.3)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    wds (1.5)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    dms (1.2)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    nas (1.0)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0]    auth (1.0)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Setting network port data format...
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Network port data format operation finished
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Allocating new client ID...
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Registered 'dms' (version 1.2) client with ID '1'
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Allocating new client ID...
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: [/dev/cdc-wdm0] Registered 'nas' (version 1.0) client with ID '1'
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB1): port attributes not fully set
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load Supported Bands: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load Power State: 'Unhandled power state: 'unknown' (255)'
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <info>  Modem: state changed (unknown -> locked)
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load SIM identifier: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load IMSI: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load list of Own Numbers: 'Couldn't get MSISDN: QMI protocol error (16): 'NotProvisioned''
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load current allowed/preferred modes: 'Loading current modes is not supported by this device'
Oct 10 21:32:13 Vostro-1015 ModemManager[707]: <warn>  couldn't load current Bands: 'QMI operation failed: Cannot send message: QMI service 'nas' version '1.1' required, got version '1.0''
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <warn> (cdc-wdm0): failed to look up interface index
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0): new Broadband device (driver: 'option1, qmi_wwan' ifindex: 0)
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0): exported as /org/freedesktop/NetworkManager/Devices/2
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0): deactivating device (reason 'managed') [2]
Oct 10 21:32:13 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (locked -> initializing)
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  (ttyUSB1): port attributes not fully set
Oct 10 21:32:21 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0) modem state changed, 'locked' --> 'initializing' (reason: unknown)
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load Supported Bands: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load Power State: 'Unhandled power state: 'unknown' (255)'
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load SIM identifier: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load IMSI: 'QMI operation failed: Cannot send message: QMI service 'dms' version '1.3' required, got version '1.2''
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load list of Own Numbers: 'Couldn't get MSISDN: QMI protocol error (16): 'NotProvisioned''
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load current allowed/preferred modes: 'Loading current modes is not supported by this device'
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <warn>  couldn't load current Bands: 'QMI operation failed: Cannot send message: QMI service 'nas' version '1.1' required, got version '1.0''
Oct 10 21:32:21 Vostro-1015 ModemManager[707]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (initializing -> disabled)
Oct 10 21:32:21 Vostro-1015 NetworkManager[803]: <info> (cdc-wdm0) modem state changed, 'initializing' --> 'disabled' (reason: unknown)


```


the syslog from debian :
```
Oct 10 20:11:22 heritiana kernel: [ 3517.462561] usb 1-1: new high-speed USB device number 5 using xhci_hcd
Oct 10 20:11:22 heritiana kernel: [ 3517.593425] usb 1-1: New USB device found, idVendor=19d2, idProduct=1233
Oct 10 20:11:22 heritiana kernel: [ 3517.593431] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Oct 10 20:11:22 heritiana kernel: [ 3517.593434] usb 1-1: Product: ZTE WCDMA Technologies MSM
Oct 10 20:11:22 heritiana kernel: [ 3517.593437] usb 1-1: Manufacturer: ZTE,Incorporated
Oct 10 20:11:22 heritiana kernel: [ 3517.593440] usb 1-1: SerialNumber: MF667ZTED0010000
Oct 10 20:11:22 heritiana systemd-udevd[8244]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 5': No such file or directory
Oct 10 20:11:22 heritiana kernel: [ 3517.895788] usb-storage 1-1:1.0: USB Mass Storage device detected
Oct 10 20:11:22 heritiana kernel: [ 3517.896337] scsi2 : usb-storage 1-1:1.0
Oct 10 20:11:22 heritiana kernel: [ 3517.896456] usbcore: registered new interface driver usb-storage
Oct 10 20:11:23 heritiana usb_modeswitch: switch device 19d2:1233 on 001/005
Oct 10 20:11:24 heritiana kernel: [ 3519.819987] usb 1-1: USB disconnect, device number 5
Oct 10 20:11:28 heritiana kernel: [ 3523.569102] usb 1-1: new high-speed USB device number 6 using xhci_hcd
Oct 10 20:11:28 heritiana kernel: [ 3523.700228] usb 1-1: New USB device found, idVendor=19d2, idProduct=1270
Oct 10 20:11:28 heritiana kernel: [ 3523.700234] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Oct 10 20:11:28 heritiana kernel: [ 3523.700237] usb 1-1: Product: ZTE WCDMA Technologies MSM
Oct 10 20:11:28 heritiana kernel: [ 3523.700240] usb 1-1: Manufacturer: ZTE,Incorporated
Oct 10 20:11:28 heritiana kernel: [ 3523.700242] usb 1-1: SerialNumber: MF667ZTED0010000
Oct 10 20:11:28 heritiana kernel: [ 3523.704964] usb-storage 1-1:1.6: USB Mass Storage device detected
Oct 10 20:11:28 heritiana systemd-udevd[8272]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 6': No such file or directory
Oct 10 20:11:28 heritiana kernel: [ 3523.705144] scsi3 : usb-storage 1-1:1.6
Oct 10 20:11:28 heritiana kernel: [ 3523.715125] usbcore: registered new interface driver usbserial
Oct 10 20:11:28 heritiana kernel: [ 3523.715642] usbcore: registered new interface driver usbserial_generic
Oct 10 20:11:28 heritiana kernel: [ 3523.715925] usbserial: USB Serial support registered for generic
Oct 10 20:11:28 heritiana kernel: [ 3523.718899] usbcore: registered new interface driver option
Oct 10 20:11:28 heritiana kernel: [ 3523.718924] usbserial: USB Serial support registered for GSM modem (1-port)
Oct 10 20:11:28 heritiana kernel: [ 3523.719108] option 1-1:1.0: GSM modem (1-port) converter detected
Oct 10 20:11:28 heritiana kernel: [ 3523.719228] usbcore: registered new interface driver cdc_wdm
Oct 10 20:11:28 heritiana kernel: [ 3523.719316] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
Oct 10 20:11:28 heritiana kernel: [ 3523.719385] option 1-1:1.1: GSM modem (1-port) converter detected
Oct 10 20:11:28 heritiana kernel: [ 3523.719477] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
Oct 10 20:11:28 heritiana kernel: [ 3523.719538] option 1-1:1.2: GSM modem (1-port) converter detected
Oct 10 20:11:28 heritiana kernel: [ 3523.719617] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
Oct 10 20:11:28 heritiana kernel: [ 3523.719677] option 1-1:1.3: GSM modem (1-port) converter detected
Oct 10 20:11:28 heritiana kernel: [ 3523.719758] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
Oct 10 20:11:28 heritiana kernel: [ 3523.719816] option 1-1:1.4: GSM modem (1-port) converter detected
Oct 10 20:11:28 heritiana kernel: [ 3523.719901] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB4
Oct 10 20:11:28 heritiana kernel: [ 3523.729785] qmi_wwan 1-1:1.5: cdc-wdm0: USB WDM device
Oct 10 20:11:28 heritiana kernel: [ 3523.730178] qmi_wwan 1-1:1.5 wwan0: register 'qmi_wwan' at usb-0000:00:14.0-1, WWAN/QMI device, 7a:1c:ab:dd:0f:41
Oct 10 20:11:28 heritiana kernel: [ 3523.733216] usbcore: registered new interface driver qmi_wwan
Oct 10 20:11:28 heritiana NetworkManager[485]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.5/net/wwan0, iface: wwan0)
Oct 10 20:11:28 heritiana NetworkManager[485]: <info> device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.5/net/wwan0, iface: wwan0): no ifupdown configuration found.
Oct 10 20:11:29 heritiana logger: usb_modeswitch: switched to 19d2:1270 on 001/006
Oct 10 20:11:29 heritiana kernel: [ 3524.706799] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Oct 10 20:11:29 heritiana kernel: [ 3524.707120] sd 3:0:0:0: Attached scsi generic sg2 type 0
Oct 10 20:11:29 heritiana kernel: [ 3524.709091] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Oct 10 20:11:29 heritiana kernel: [ 3524.754310] sd 3:0:0:0: ioctl_internal_command return code = 8070000
Oct 10 20:11:29 heritiana kernel: [ 3524.754314]    : Sense Key : Hardware Error [current] 
Oct 10 20:11:29 heritiana kernel: [ 3524.754317]    : Add. Sense: No additional sense information
Oct 10 20:11:29 heritiana kernel: [ 3524.798336] sd 3:0:0:0: ioctl_internal_command return code = 8070000
Oct 10 20:11:29 heritiana kernel: [ 3524.798339]    : Sense Key : Hardware Error [current] 
Oct 10 20:11:29 heritiana kernel: [ 3524.798343]    : Add. Sense: No additional sense information


```

what to do?

thanks in advance

---

### Post by azertyh on 2015-10-24
hello,
solved by installing modemmanager.

---

