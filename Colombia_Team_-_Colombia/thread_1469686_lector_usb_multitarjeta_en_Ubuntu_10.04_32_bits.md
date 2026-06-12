---
title: "lector usb multitarjeta en Ubuntu 10.04 32 bits"
date: 2010-05-02
forum: Colombia Team - Colombia
---

### Post by jwcalderon on 2010-05-02
Cordial saludo,

He tenido problemas con varios dispositivos USB, lectores multitarjeta, Ubuntu (10.04 LTS y anteriores) reconoce los dispositivos, pero no procede a realizar el proceso de mount. A continuacion listo la informacion que he recopilado del sistema.

Les agrdezco de antemano la ayuda.


-- ----------------------------------------------------
-- Antes de conectar el Lector Multitarjeta USB Sandisk
-- ----------------------------------------------------

usuario@computador:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:4003 Dell Computer Corp. Axim X30
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-- ------------------------------------------------------
-- Despues de conectar el Lector Multitarjeta USB Sandisk
-- ------------------------------------------------------

usuario@computador:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:4003 Dell Computer Corp. Axim X30
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 036: ID 0781:8889 SanDisk Corp. SDDR-88 Imagemate 8-in-1 Reader[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-- ---------------------------------------------------------------------------------
-- Informacion completa de lsusb -vv (solo para el dispositivo problema)
-- ---------------------------------------------------------------------------------

Bus 001 Device 048: ID 0781:8889 SanDisk Corp. SDDR-88 Imagemate 8-in-1 Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x8889 SDDR-88 Imagemate 8-in-1 Reader
  bcdDevice           91.44
  iManufacturer           3 
  iProduct                4 
  iSerial                 5 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
  
-- -------------------------------------------------------------------------------------------
-- Luego espere alrededor de 2 minutos para que el comando dmesg trajera toda la informacion :
-- -------------------------------------------------------------------------------------------

usuario@computador:~$ dmesg 
[ 6519.504027] usb 1-5: new high speed USB device using ehci_hcd and address 36
[ 6519.654004] usb 1-5: configuration #1 chosen from 1 choice
[ 6519.654798] scsi36 : SCSI emulation for USB Mass Storage devices
[ 6519.654988] usb-storage: device found at 36
[ 6519.654991] usb-storage: waiting for device to settle before scanning
[ 6524.652549] usb-storage: device scan complete
[ 6524.653916] scsi 36:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[ 6546.047025] usb 1-5: USB disconnect, address 36
[ 6546.047042] scsi 36:0:0:1: Device offlined - not ready after error recovery
[ 6546.047644] sd 36:0:0:0: Attached scsi generic sg3 type 0
[ 6546.050370] sd 36:0:0:0: [sdc] READ CAPACITY failed
[ 6546.050375] sd 36:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6546.050380] sd 36:0:0:0: [sdc] Sense not available.
[ 6546.050407] sd 36:0:0:0: [sdc] Write Protect is off
[ 6546.050411] sd 36:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 6546.050414] sd 36:0:0:0: [sdc] Assuming drive cache: write through
[ 6546.050820] sd 36:0:0:0: [sdc] READ CAPACITY failed
[ 6546.050824] sd 36:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6546.050829] sd 36:0:0:0: [sdc] Sense not available.
[ 6546.050845] sd 36:0:0:0: [sdc] Assuming drive cache: write through
[ 6546.050848] sd 36:0:0:0: [sdc] Attached SCSI removable disk
[ 6546.345533] usb 1-5: new high speed USB device using ehci_hcd and address 37
[ 6546.490537] usb 1-5: configuration #1 chosen from 1 choice
[ 6546.491277] scsi37 : SCSI emulation for USB Mass Storage devices
[ 6546.503248] usb-storage: device found at 37
[ 6546.503251] usb-storage: waiting for device to settle before scanning
[ 6551.500580] usb-storage: device scan complete
[ 6551.616525] usb 1-5: reset high speed USB device using ehci_hcd and address 37
[ 6551.755965] scsi 37:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[ 6573.100720] usb 1-5: reset high speed USB device using ehci_hcd and address 37
[ 6583.348525] usb 1-5: reset high speed USB device using ehci_hcd and address 37
[ 6599.544329] usb 1-5: USB disconnect, address 37
[ 6599.544336] scsi 37:0:0:1: Device offlined - not ready after error recovery
[ 6599.545132] sd 37:0:0:0: Attached scsi generic sg3 type 0
[ 6599.546046] sd 37:0:0:0: [sdc] READ CAPACITY failed
[ 6599.546050] sd 37:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6599.546055] sd 37:0:0:0: [sdc] Sense not available.
[ 6599.546072] sd 37:0:0:0: [sdc] Write Protect is off
[ 6599.546076] sd 37:0:0:0: [sdc] Mode Sense: 2e 2e 2f 2e
[ 6599.546079] sd 37:0:0:0: [sdc] Assuming drive cache: write through
[ 6599.549878] sd 37:0:0:0: [sdc] READ CAPACITY failed
[ 6599.549883] sd 37:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6599.549888] sd 37:0:0:0: [sdc] Sense not available.
[ 6599.550449] sd 37:0:0:0: [sdc] Assuming drive cache: write through
[ 6599.550454] sd 37:0:0:0: [sdc] Attached SCSI removable disk
[ 6599.844031] usb 1-5: new high speed USB device using ehci_hcd and address 38
[ 6599.989960] usb 1-5: configuration #1 chosen from 1 choice
[ 6599.990748] scsi38 : SCSI emulation for USB Mass Storage devices
[ 6599.990940] usb-storage: device found at 38
[ 6599.990943] usb-storage: waiting for device to settle before scanning
[ 6604.989007] usb-storage: device scan complete
[ 6604.990373] scsi 38:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[ 6626.100026] usb 1-5: reset high speed USB device using ehci_hcd and address 38
[ 6626.168341] usb 1-5: USB disconnect, address 38
[ 6626.168358] scsi 38:0:0:1: Device offlined - not ready after error recovery
[ 6626.169211] sd 38:0:0:0: Attached scsi generic sg3 type 0
[ 6626.169487] sd 38:0:0:0: [sdc] READ CAPACITY failed
[ 6626.169490] sd 38:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6626.169496] sd 38:0:0:0: [sdc] Sense not available.
[ 6626.169514] sd 38:0:0:0: [sdc] Write Protect is off
[ 6626.169517] sd 38:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 6626.169520] sd 38:0:0:0: [sdc] Assuming drive cache: write through
[ 6626.169699] sd 38:0:0:0: [sdc] READ CAPACITY failed
[ 6626.169702] sd 38:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6626.169706] sd 38:0:0:0: [sdc] Sense not available.
[ 6626.169722] sd 38:0:0:0: [sdc] Assuming drive cache: write through
[ 6626.169726] sd 38:0:0:0: [sdc] Attached SCSI removable disk
[ 6626.292527] usb 1-5: new high speed USB device using ehci_hcd and address 39
[ 6626.437968] usb 1-5: configuration #1 chosen from 1 choice
[ 6626.438769] scsi39 : SCSI emulation for USB Mass Storage devices
[ 6626.438975] usb-storage: device found at 39
[ 6626.438977] usb-storage: waiting for device to settle before scanning
[ 6631.437138] usb-storage: device scan complete
[ 6631.552047] usb 1-5: reset high speed USB device using ehci_hcd and address 39
[ 6631.692659] scsi 39:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0


-- -----------------------------------------------------------------------------------------
-- Pueden notar que desde la marca [ 6519.504027] hasta [ 6546.050848] se repite 
-- mientras el dispositivo sigue conectado.
-- -----------------------------------------------------------------------------------------

-- -----------------------------------------------------------------------------------------------
-- En algun momento pense que se trataba de "montar" el la misma particion logica que el DVD, pero :
-- -----------------------------------------------------------------------------------------------

jwcalderon@flia:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda1             450G  344G   83G  81% /                           -> Disco duro principal
none                  2,0G  356K  2,0G   1% /dev
none                  2,0G  4,3M  2,0G   1% /dev/shm
none                  2,0G  192K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
none                  450G  344G   83G  81% /var/lib/ureadahead/debugfs
/dev/sdb1             299G   85G  214G  29% /media/C000F5B000F5AD92     -> Disco duro Adicional
/dev/sr0              3,8G  3,8G     0 100% /media/VBoxApplianceWinXP   -> DVD

Gracias.

---

