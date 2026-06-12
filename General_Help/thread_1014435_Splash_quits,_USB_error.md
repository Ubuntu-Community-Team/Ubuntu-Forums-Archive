---
title: "Splash quits, USB error"
date: 2008-12-17
forum: General Help
---

### Post by schnauzer93 on 2008-12-17
When I boot up Intrepid, my splash screen quits and gives me an error. 

dmesg | grep -i usb```
[    2.559552] usbcore: registered new interface driver usbfs
[    2.559570] usbcore: registered new interface driver hub
[    2.559780] usbcore: registered new device driver usb
[    2.561389] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.229984] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.288098] usb usb1: configuration #1 chosen from 1 choice
[    4.288126] hub 1-0:1.0: USB hub found
[    4.389590] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    4.448113] usb usb2: configuration #1 chosen from 1 choice
[    4.448141] hub 2-0:1.0: USB hub found
[    4.549083] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.609071] usb usb3: configuration #1 chosen from 1 choice
[    4.609475] hub 3-0:1.0: USB hub found
[    4.817996] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    4.876558] usb usb4: configuration #1 chosen from 1 choice
[    4.876980] hub 4-0:1.0: USB hub found
[    4.981096] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    5.040587] usb usb5: configuration #1 chosen from 1 choice
[    5.041030] hub 5-0:1.0: USB hub found
[    7.908020] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   10.996020] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   14.084019] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   17.172531] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   17.172588] hub 3-0:1.0: unable to enumerate USB device on port 1

```

However, all my USB ports work perfectly. I have, however, switched my front ports' motherboard cable to the second slot since while it was plugged into the first slot, one of them wouldn't work. Any ideas?

---

