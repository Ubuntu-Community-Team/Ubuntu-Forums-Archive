---
title: "Unstable bluetooth connection with Nokia 6300"
date: 2009-02-08
forum: General Help
---

### Post by stocksy on 2009-02-08
I'm trying to connect my Nokia 6300 to an install of 8.04, and I'm not having much luck.

Using a D-Link DBT-122 adapter, the phone connects at first, but the connection immediately dies and is then re-established a few seconds later.  Here is one iteration of this process from the syslog:

```

Feb  8 17:51:37 pabx-gw kernel: [ 3902.613894] usb 1-1: USB disconnect, address 5
Feb  8 17:51:38 pabx-gw hcid[4284]: HCI dev 0 down
Feb  8 17:51:38 pabx-gw hcid[4284]: Stopping security manager 0
Feb  8 17:51:38 pabx-gw hcid[4284]: Device hci0 has been disabled
Feb  8 17:51:38 pabx-gw hcid[4284]: HCI dev 0 unregistered
Feb  8 17:51:38 pabx-gw hcid[4284]: Unregister path: /org/bluez/hci0
Feb  8 17:51:38 pabx-gw hcid[4284]: Device hci0 has been removed
Feb  8 17:51:39 pabx-gw kernel: [ 3904.779897] usb 1-1: new full speed USB device using uhci_hcd and address 6
Feb  8 17:51:40 pabx-gw kernel: [ 3905.187647] usb 1-1: configuration #1 chosen from 1 choice
Feb  8 17:51:40 pabx-gw hcid[4284]: HCI dev 0 registered
Feb  8 17:51:40 pabx-gw hcid[4284]: HCI dev 0 up
Feb  8 17:51:40 pabx-gw hcid[4284]: Device hci0 has been added
Feb  8 17:51:40 pabx-gw hcid[4284]: Starting security manager 0
Feb  8 17:51:41 pabx-gw hcid[4284]: Can't read version info for hci0: Connection timed out (110)
Feb  8 17:51:43 pabx-gw hcid[4284]: Sending getting name command failed: Connection timed out (110)
Feb  8 17:51:43 pabx-gw hcid[4284]: Getting name failed with status 0xd7
Feb  8 17:51:43 pabx-gw hcid[4284]: return_link_keys (sba=00:80:C8:35:2D:14, dba=00:0A:95:00:A3:13)

```

I tried upgrading to intrepid, but that didn't work at all because of this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

Other potentially pertinent information:

- The machine is a virtual machine running in VMWare server 1.0.8
- The application doing the connecting is Asterisk (with chan_mobile.so)
- There is no GUI - used the Ubuntu server .iso

I'm completely stuck, *any* suggestions would be welcomed!

---

### Post by marquivon on 2009-03-31
Were you able to find out a solution to this?

---

### Post by stocksy on 2009-03-31
No, I gave up in the end.  Sorry, but I have no advice to give.

---

