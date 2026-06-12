---
title: "How to sync WM2003-SE PDA in Intrepid"
date: 2009-01-04
forum: General Help
---

### Post by bakra01 on 2009-01-04
I know there has been written a lot about syncing a PDA in Ubuntu, and I've got the feeling I tried them all. But after weeks of struggling still not working. :confused:
I'm afraid with all the trying I did install things I don't need or I removed things I need.

This is my configuration:
- WM2003-SE PDA (Yakumo DeltaX)
- Ubuntu 8.10
- connected trough USB
- Thunderbird (or if syncing with Thunderbird is impossible Evolution)

This is a part of what I get with DMESG:

[  177.458708] usb 2-1.1: USB disconnect, address 4
[  177.463822] ipaq 2-1.1:1.0: device disconnected
[  184.105627] usb 2-1.1: new full speed USB device using uhci_hcd and address 5
[  184.649349] usb 2-1.1: configuration #1 chosen from 1 choice
[  184.652056] ipaq 2-1.1:1.0: PocketPC PDA converter detected
[  184.656027] usb 2-1.1: PocketPC PDA converter now attached to ttyUSB1

So, the device is recognised, but in SynCE Tray Icon I've got "no dvice connected"

When I hit "Sync" or "Resync" in Multisync nothing happens.

Maybe good to know: I use Virtualbox OSE and that's why I use a virtual NIC, wich is bridged with the real NIC. I don't know if this will interfere with the connection of the PDA.


Can someone please tell me step by step how to get this working?
Any help wil be appriciated.

---

### Post by bakra01 on 2009-01-28
Nobody using WM2003SE PDA in Ubuntu????

---

### Post by Bupsss on 2009-01-28
had the same problem just yesterday, did you install Synce-gnomevfs ?
i also did a soft reset on the pocketpc, while plugged in.

---

### Post by bakra01 on 2009-01-31
I did install it again.
In the log it says: Connection OK; no new changes reported.
But it doesn't sync my apointments

---

