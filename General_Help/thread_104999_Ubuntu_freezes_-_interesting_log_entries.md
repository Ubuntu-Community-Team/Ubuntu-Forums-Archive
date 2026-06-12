---
title: "Ubuntu freezes - interesting log entries"
date: 2005-12-17
forum: General Help
---

### Post by billd on 2005-12-17
I'm not sure saying "ubuntu freezes" is correct -- more like "X freezes", I guess.

Symptoms: the mouse can move, but clicking on something either does nothing, or does it about a minute later.  Ctrl-Alt-Backspace will make X disappear but give no prompt (just black).

This has been happening about once or twice per day.  The last couple of times I've been studying the logs.  One recurring theme is "**gdm_slave_xioerror_handler**".  Another interesting thing is a "ghost" iPod being found while I was nowhere near the computer.  Summarized below. Can anybody help me figure out what's happening?

---

When I came home last night, the panel clock was frozen at 2:28 PM.  Syslog shows this at about that time:
```
Dec 16 14:28:49 localhost shutdown[20325]: shutting down for system halt
Dec 16 14:28:53 localhost gconfd (bill-8692): Received signal 15, shutting down cleanly
Dec 16 14:28:53 localhost gconfd (bill-8692): Exiting
Dec 16 14:28:53 localhost gdm[8041]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

Interestingly, twelve minutes before that, the following was written to the messages log:

```
Dec 16 14:16:46 localhost kernel: [4345251.950000] usb 4-5: new high speed USB device using ehci_hcd and address 7
Dec 16 14:16:58 localhost kernel: [4345263.078000] scsi4 : SCSI emulation for USB Mass Storage devices
Dec 16 14:16:58 localhost usb.agent[20137]:      usb-storage: already loaded
Dec 16 14:17:05 localhost kernel: [4345270.488000]   Vendor: Apple     Model: iPod              Rev: 1.62
Dec 16 14:17:05 localhost kernel: [4345270.488000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Dec 16 14:17:05 localhost kernel: [4345270.493000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Dec 16 14:17:05 localhost kernel: [4345270.493000] sdb: Write Protect is off
Dec 16 14:17:05 localhost kernel: [4345270.493000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Dec 16 14:17:12 localhost kernel: [4345270.493000] sdb: Write Protect is off
Dec 16 14:17:20 localhost kernel: [4345270.493000]  /dev/scsi/host4/bus0/target0/lun0: p1 p2
Dec 16 14:17:20 localhost kernel: [4345270.493000] Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
Dec 16 14:17:20 localhost scsi.agent[20203]:      sd_mod: loaded sucessfully (for disk)
```

Interesting thing is, **I was not home and my iPod was with me!**  How the heck did it decide it was suddenly there??

Then just one hour ago I got the freeze problem again.  Here are the entries that were written as it happened:

```
Dec 17 16:49:50 localhost gdm[7856]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Dec 17 16:49:51 localhost kernel: [4296259.041000] mtrr: base(0x88020000) is not aligned on a size(0x400000) boundary
Dec 17 16:49:51 localhost shutdown[9248]: shutting down for system halt

```

---

### Post by billd on 2005-12-20
(bump)

Any ideas? thx.

---

### Post by Mustard on 2006-01-20
First thing I would do is run the memtest from the grub menu to check for bad RAM.  That may not be the problem, but I would like to eliminate that as a cause of the Fatal X error.

---

