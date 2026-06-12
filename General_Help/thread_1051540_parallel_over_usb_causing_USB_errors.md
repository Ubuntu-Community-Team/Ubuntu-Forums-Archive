---
title: "parallel over usb causing USB errors"
date: 2009-01-26
forum: General Help
---

### Post by wadesmart on 2009-01-26
I have a HP LaserJet 4050 that has been working very well with my computer. A few months back I ran out of ink so its been sitting until last week. I put the ink in and I couldnt print. 

I was checking things out and I found this:

```
E [23/Jan/2009:09:25:39 -0600] [Job 18] No %%BoundingBox: comment in header!
E [23/Jan/2009:09:32:21 -0600] [Job 18] No %%BoundingBox: comment in header!
E [23/Jan/2009:09:32:21 -0600] [Job 18] Could initialize HAL daemon: (null)
E [23/Jan/2009:09:50:41 -0600] [Job 19] No %%BoundingBox: comment in header!
E [23/Jan/2009:09:51:32 -0600] Cancel-Job: Unauthorized
E [23/Jan/2009:09:51:50 -0600] Pause-Printer: Unauthorized
E [23/Jan/2009:09:51:50 -0600] Pause-Printer: Unauthorized
E [23/Jan/2009:09:52:02 -0600] Resume-Printer: Unauthorized 
```

```
In /var/log/syslog I have hundreds of lines with this:
Jan 23 10:23:17 wadesmart kernel: [ 3099.402989] usb 1-1: new full speed USB device using uhci_hcd and address 41
Jan 23 10:23:17 wadesmart kernel: [ 3099.814140] usb 1-1: device not accepting address 41, error -71
Jan 23 10:23:17 wadesmart kernel: [ 3099.925926] usb 1-1: new full speed USB device using uhci_hcd and address 42
Jan 23 10:23:18 wadesmart kernel: [ 3100.333105] usb 1-1: device not accepting address 42, error -71 
```

In cups the address of the printer is:
Device URI:
hal:///org/freedesktop/Hal/devices/usb_device_4348_5584_noserial_if0_printer_noserial 

Now, if I have the cable plugged in to any of the six usb ports with or without the printer on, it immediately starts adding the above entries to the system log.

Wade

---

