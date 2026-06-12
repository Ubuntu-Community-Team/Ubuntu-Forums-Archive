---
title: "NexStar enclosure firewire not mounting"
date: 2006-06-06
forum: Desktop Environments
---

### Post by hectorC on 2006-06-06
EDIT: Sorry, too late I found this should have been posted under the hardware section. Could someone move it? Sorry. 


Hi,

In a freshly installed Dapper I can't get my NexStar hard drive enclosure to mount using firewire. This enclosure uses the Prolific PL-3507A chipset combo (it has both usb and firewire). Using the usb it mounts with no problems, but it would be convenient for me to use firewire instead. This is dmesg's output:

[4295334.194000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4295335.122000] ieee1394: Error parsing configrom for node 0-00:1023
[4295335.122000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4295338.851000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e700030e5][4295338.851000] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4295340.055000] ieee1394: sbp2: Logged into SBP-2 device
[4295340.055000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048][4295345.555000] ieee1394: sbp2: aborting sbp2 command
[4295345.555000]  0:0:0:0:
[4295345.555000]         command: Inquiry: 12 00 00 00 24 00
[4295355.555000] ieee1394: sbp2: aborting sbp2 command
[4295355.555000]  0:0:0:0:
[4295355.555000]         command: Test Unit Ready: 00 00 00 00 00 00
[4295355.555000] ieee1394: sbp2: reset requested
[4295355.555000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[4295365.555000] ieee1394: sbp2: aborting sbp2 command
[4295365.555000]  0:0:0:0:
[4295365.555000]         command: Test Unit Ready: 00 00 00 00 00 00
[4295365.555000] ieee1394: sbp2: reset requested
[4295365.555000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[4295385.556000] ieee1394: sbp2: aborting sbp2 command
[4295385.556000]  0:0:0:0:
[4295385.556000]         command: Test Unit Ready: 00 00 00 00 00 00
[4295385.556000] ieee1394: sbp2: reset requested
[4295385.556000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[4295405.557000] ieee1394: sbp2: aborting sbp2 command
[4295405.557000]  0:0:0:0:
[4295405.557000]         command: Test Unit Ready: 00 00 00 00 00 00
[4295405.557000]  0:0:0:0: scsi: Device offlined - not ready after error recovery
[4295405.557000] ieee1394: sbp2: scsi_add_device failed (-19)
[4295405.557000] scsi1 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4295426.761000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[4295426.762000] sbp2: probe of 0050770e700030e5-0 failed with error -16

Thank you!


Hector.

---

### Post by hectorC on 2006-06-11
BUMP!

Anyone have an idea?

Thanks!


Hector.

---

### Post by miceagol on 2006-06-19
I have a similar output in dmesg, and the same problem.

Anyone???

---

