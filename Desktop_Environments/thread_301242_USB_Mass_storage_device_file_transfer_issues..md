---
title: "USB Mass storage device file transfer issues."
date: 2006-11-16
forum: Desktop Environments
---

### Post by Peepsalot on 2006-11-16
I just got a USB cable that works with my phone for transferring files (mp3s, wallpapers, ringtones, java apps, etc.).  When I plug it in, it connects as a mass storage device and I can easily drag and drop files.

The copying of the files is almost instantaneous, but I think this is where the problem lies.  Instead of giving an actual progress bar, I think it is pretending to be finished while it continues to copy in the background.  The problem with this is I have no idea when I can finally disconnect my phone.  

I do a right click on the device and eject in nautilus, and it instantly disappears from the menu.  This would lead me to believe that it is safe to disconnect.  Nope, as soon as I do an error pops up that it could not eject the device properly(pretty sure it was still waiting for transfers).

So I can't rely on the file copy dialog to tell me when it's done, and I can't rely on the eject function to tell me when it's done.  Is there anything I can rely on?

I just really hope this is a bug and not how it was designed to behave.  Can anyone shed some light on the subject?

---

### Post by 3rdalbum on 2006-11-16
On Dapper, if I try to unmount before the copying has truly finished, it pops up an "indeterminate" progress bar, saying that it is still writing data to the device. When it's really finished, the box disappears and the device unmounts.

This feature was not present on Breezy... I never thought it had been removed from Edgy.

As a stop-gap solution, you should try unmounting from the terminal. Assuming that the mount point is /media/usbdisk:

```
sudo umount /media/usbdisk
pumount /media/usbdisk
```

I can't quite remember: Either the commands give an error message if there's still copying to do, or they don't return until the copying is finished.

---

