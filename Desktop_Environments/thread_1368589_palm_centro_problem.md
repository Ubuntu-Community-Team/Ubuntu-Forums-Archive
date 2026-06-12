---
title: "palm centro problem"
date: 2009-12-30
forum: Desktop Environments
---

### Post by horowitz on 2009-12-30
Hi

I have just acquired a palm centro phone and decided to try syncing it using ubuntu 9.10 over usb. The moment I plug it into the usb port, the centro reboots, and continues to reboot until I unplug it. Anyone have any ideas about this behaviour.

Thanks

Bill

---

### Post by falconindy on 2009-12-30
Similar behavior here. Eventually gave in and it gets sync'ed through a Windows VM now.

---

### Post by JSeymour on 2009-12-31
Hmmm... My Palm Centro does not do that.  Ubuntu 9.10 Desktop.

---

### Post by Edifier1007 on 2010-01-27
Hi all,

Any positive update on this ? 

I have started getting this issue over the weekend. [ I upgraded to 9.10 over the weekend. ]

For me it worked the first time I tried doing the Hotsync and then its been rebooting. 

Works well on RHEL and Mac. I tried sync on a Mac and then connected to 9.10 - it did not reboot at that time. I need to try that again to see if it works. May be it will help locate the issue. To me it seems like USB connection issue.

---

### Post by Edifier1007 on 2010-01-27
Update : I tried the test of syncing with Mac and then connecting to 9.10 - no luck. Still reboots !! :(

---

### Post by Edifier1007 on 2010-01-28
Getting these messages in /var/log/messages ...

Jan 28 15:05:03 tlaptop kernel: [  263.548054] usb 3-2: new full speed USB device using uhci_hcd and address 14
Jan 28 15:05:03 tlaptop kernel: [  263.722149] usb 3-2: configuration #1 chosen from 1 choice
Jan 28 15:05:03 tlaptop kernel: [  263.727028] visor 3-2:1.0: Handspring Visor / Palm OS converter detected
Jan 28 15:05:03 tlaptop kernel: [  263.727101] usb 3-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jan 28 15:05:03 tlaptop kernel: [  263.727141] usb 3-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jan 28 15:05:07 tlaptop kernel: [  267.000138] usb 3-2: USB disconnect, address 14
Jan 28 15:05:07 tlaptop kernel: [  267.000444] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jan 28 15:05:07 tlaptop kernel: [  267.000570] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jan 28 15:05:07 tlaptop kernel: [  267.000596] visor 3-2:1.0: device disconnected

Also, found out that Centro is identified as 'Palm Inc...' Device and not a 'Palm Handheld' !!

---

### Post by Edifier1007 on 2010-03-01
Ok. Have this resolved for me. Someone in Palm forums gave me a tip to disable / remove modem-manager and it works for me. 

Reboot issue is resolved and I can now sync the phone with 9.10.

---

### Post by Raval on 2010-07-02
Hey guys I'm looking for a phone that I can sync with Evolution Calendar, Contacts and To do list. does the the Centro fit the bill?

---

