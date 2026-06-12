---
title: "Using camera as a card reader/writer?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by sleeping on 2006-08-01
Hello,

I am not trying to make a Windows/Ubuntu comparison here. I'm just looking for a features I liked in Windows and that I'd like to find in Ubuntu too... I'm pretty sure it's somewhere in there, I just don't know where...

In Windows, when I plugged the USB cable from my digital camera (Kodak CX6230), Windows would mount the camera as some sort of removable device that I could both read from and write to.

With Ubuntu, so far, all I've managed to do when I plug the USB cable from my camera is get an "Import Photos" dialog that allows me to transfer files from the camera to my computer, but I can't find how to copy files from my computer to my digital camera.

How can I copy files to my digital camera without having a card reader?

Thanks a bunch.

---

### Post by Dubbayoo on 2006-08-01
I've never tried it since I have a card reader. I would guess you'd need to create a mount point then figure out which device the camera is assigned and mount it accordingly. I don't believe it gets a mount point on its own.

---

### Post by sleeping on 2006-08-01
Ok, that's all good and it makes sense. However, how do I know which device is assigned to the cameara? I tried a dirty trick of plugging in the camera, then do a sudo updatedb, and then locate with a filename on the camera, but it didn't find anything.

I don't have any usb* listed in /dev. When the camera is plugged, the camera doesn't show in the output of df.

```

$ tail /var/log/messages

Aug  1 22:09:46 homecomputer kernel: [17180586.264000] usb 1-2: new full speed USB device using uhci_hcd and address 4

$ locate uhci

/lib/modules/2.6.15-26-386/kernel/drivers/usb/host/uhci-hcd.ko

```

All I gather from the above is that the camera got picked up by a USB driver, but I have no idea what to do with a uhci-hcd.ko file.


I guess I could try to mount every devices one after another, but I might still be here tomorrow...


Any pointer would be greatly appreciated.

---

