---
title: "device node not assigned for my Palm"
date: 2005-08-05
forum: Desktop Environments
---

### Post by dlee27 on 2005-08-05
Hi,

I just got Fossil Wrist PDA and I'm trying to sync it with Ubuntu. When I connect it and press hotsync dmesg says something like this:

```

 localhost kernel: usb 1-2: new full speed USB device using ohci_hcd and address 8

```

But kernel doesn't assign device node. I searched a little about palm sync and everyone said that it's assigned something like /dev/ttyUSB0. 
What should I look for?
Thanks.

---

### Post by dave9191 on 2005-08-05
Go to your /dev folder and plug the device in. A device such as ttyUSB0 should appear in there. Of course if you have other usb devices they will be ttyUSB1, etc. Put that path into your sync program as the location of your device. 

Dave

---

### Post by dlee27 on 2005-08-05
The problem is /dev/ttyUSB* does not appear.

I even wrote custom udev rule like the followings but it doesn't create /dev/pilot, either. Gnome-pilot looks for /dev/pilot, btw.
```

SYSFS{product}="Wrist PDA", SYSFS{idVendor}="0e67", NAME="pilot", MODE="666"

```

Thanks.

---

### Post by dave9191 on 2005-08-06
Maybe its being assigned another location? Does anything extra show up in the /dev/ folder? Becuase it is detecting it, its strange that it doesnt assign anything to it. 

Dave

---

### Post by Juergen on 2005-08-06
For my Tungsten E2 /dev/ttyUSB[01] are only created when I press the sync-buttton on the cable, not by just connecting the Palm.
Try
```
tail -f /var/log/messages
``` and look what happens when you press the button
Look at /dev before the sync-process is aborted.

Maybe [http://www.gadgetreview.com/guides/palm-under-linux.html](http://www.gadgetreview.com/guides/palm-under-linux.html) can also help.

And ttyUSB0 is for whatever ;-) The syncing is done via ttyUSB1.

---

### Post by dlee27 on 2005-08-07
[QUOTE=Juergen]For my Tungsten E2 /dev/ttyUSB[01] are only created when I press the sync-buttton on the cable, not by just connecting the Palm.
Try
```
tail -f /var/log/messages
``` and look what happens when you press the button
Look at /dev before the sync-process is aborted.

Maybe [http://www.gadgetreview.com/guides/palm-under-linux.html](http://www.gadgetreview.com/guides/palm-under-linux.html) can also help.

And ttyUSB0 is for whatever ;-) The syncing is done via ttyUSB1.[/QUOTE]

I know it only appears when hotsync is pressed. The system message when I hotsynced is on my first message. Kernel just doesn't assign anything. I'm not getting any ttyUSB*. udevinfo showed my Wrist PDA correctly so I used that info to create a  custom udev file but still nothing. 

Thanks.

---

