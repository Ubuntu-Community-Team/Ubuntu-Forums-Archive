---
title: "Evolution Gnome-pilot and palm (Sony Clie SJ30) problems"
date: 2007-03-28
forum: Desktop Environments
---

### Post by lordphoenix on 2007-03-28
Hi,
One more time like at every new release of Ubuntu I try to sync my PDA 5Sony clie SJ30) with evolution but like previous time there's no way to do it. 

I hoped that this time it coulkd be succesfull when I saw the new usb: method to connect my PDA but it doesn't succed. 

I've  checked in /dev/ dir and there is no pilot or ttyUSBx file so even JPilot can't be used. 

Can I hope to be able to sync my palm with evolution ?

Thanks for help 

 here is lsusb output 
```
Bus 001 Device 017: ID 054c:0066 Sony Corp. Clie PEG-N7x0C/PEG-T425 PalmOS PDA Serial
```

Message log 
```
Mar 28 14:01:35 jupiter kernel: [13192.036000] usb 1-2.4: new full speed USB device using uhci_hcd and address 16
Mar 28 14:01:35 jupiter kernel: [13192.160000] usb 1-2.4: configuration #1 chosen from 1 choice
Mar 28 14:02:35 jupiter kernel: [13252.816000] usb 1-2.4: USB disconnect, address 16
```

and Syslog 
```
Mar 28 14:01:35 jupiter kernel: [13192.036000] usb 1-2.4: new full speed USB device using uhci_hcd and address 16
Mar 28 14:01:35 jupiter kernel: [13192.160000] usb 1-2.4: configuration #1 chosen from 1 choice
Mar 28 14:01:35 jupiter NetworkManager: <debug info>^I[1175083295.753317] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial'). 
Mar 28 14:01:36 jupiter NetworkManager: <debug info>^I[1175083296.591712] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial_if0'). 
Mar 28 14:01:37 jupiter NetworkManager: <debug info>^I[1175083297.147634] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial_usbraw'). 
Mar 28 14:02:35 jupiter kernel: [13252.816000] usb 1-2.4: USB disconnect, address 16
Mar 28 14:02:35 jupiter NetworkManager: <debug info>^I[1175083355.899268] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial_if0'). 
Mar 28 14:02:35 jupiter NetworkManager: <debug info>^I[1175083355.905442] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial_usbraw'). 
Mar 28 14:02:35 jupiter NetworkManager: <debug info>^I[1175083355.910865] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_66_noserial'). 
```

---

### Post by lordphoenix on 2007-04-03
if it can help I've started gpilotd from a console and I've got this message :

```

gpilotd-Message: gnome-pilot 2.0.15 starting...
gpilotd-Message: compiled for pilot-link version 0.12.1
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] 

(gnome-pilot:32208): libgpilotdcm-WARNING **: Le nombre de périphériques est configuré à 0

(gnome-pilot:32208): libgpilotdcm-WARNING **: Aucun périphériques accessibles disponible

(gnome-pilot:32208): libgpilotdcm-WARNING **: Number of PDAs is configured to 0
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 0
gpilotd-Message: Extinction des périphériques
gpilotd-Message: Relecture de la configuration...

(gnome-pilot:32208): libgpilotdcm-WARNING **: Number of PDAs is configured to 0
gpilotd-Message: Regarde Cradle (usb:)
gpilotd-Message: corba: get_user_info(cradle=Cradle,survival=0,timeout=0)
gpilotd-Message: assigned handle num 1
gpilotd-Message: Found 4766, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0502, 0736
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 091e, 0004
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 115e, f100
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0100
gpilotd-Message: Using net FALSE
gpilotd-Message: Found 082d, 0200
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0300
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0c88, 0021
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0002
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0003
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0020
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0031
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0040
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0050
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0060
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0061
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0070
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0080
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 8001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 6601
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0038
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0066
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0095
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 009a
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00c9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00da
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00e9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0144
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0169
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 12ef, 0100
gpilotd-Message: Using net TRUE
gpilotd-Message: setting PILOTRATE=57600

(gnome-pilot:32208): gpilotd-WARNING **: An error occurred while getting the PDA's system data

(gnome-pilot:32208): gpilotd-WARNING **: error -201 from pi_close.


```

I think that message "An error occurred while getting the PDA's" is significant but what does it mean exactly?

Anyone has an idea?

---

### Post by mginou on 2007-04-25
I have exactly the same problem with my Palm TungstenW:

gpilotd-WARNING **: An error occurred while getting the PDA's system data

---

### Post by lordphoenix on 2007-04-27
I've solved the problem using visor module wich is no longer loaded on start

---

### Post by cdawg on 2008-01-04
It took forever but I found a note on some obscure website after hours of digging to solve this problem by setting the USB timeout to 0 in the gnome-applet. 

It actually worked for me.

---

