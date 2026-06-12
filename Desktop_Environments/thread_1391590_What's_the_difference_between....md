---
title: "What's the difference between..."
date: 2010-01-27
forum: Desktop Environments
---

### Post by Moozillaaa on 2010-01-27
... 'Unmount Drive', and 'Safely Remove Hardware'???

Ubuntu 9.10

---

### Post by routtj on 2010-01-27
Zero.

---

### Post by aysiu on 2010-01-27
*Unmount* simply unmounts the drive from the mount point. It actually also, funnily enough, makes it safe to remove. But if you look in Places, you will still see the drive, which you can select again to remount.

*Safely Remove* will power down the device (so if your USB key, for example, has a light, the light will turn off). If you look in Places, it should be gone, so you can't remount it without physically removing the device and then physically plugging it back in again.

---

### Post by mcduck on 2010-01-27
One important difference is that if you have a device with many partitions, "unmount" will only unmount the partition you selected, while "Eject" and "Safely Remove Drive" will unmount *all* partitions of that drive.

---

### Post by rossmoore on 2010-01-27
That's interesting, I'd always wondered about those differences. Unmounting all partitions on the drive is pretty handy I guess - although it's not obvious that this is what the option does.

Sometimes all 3 are presented as options. When they are (I'll try and find an example if you don't believe me!), what's the difference between "Eject" and "Safely Remove"? Does one unmount all drives and the other do that AND power down the device? Which one does which?!

---

### Post by Rhubarb on 2010-01-27
I know eject can eject the tray on your optical drive, but I'm not sure why that option appears for flash media also.

---

### Post by rossmoore on 2010-01-27
Yeah, that's my point. "Eject" doesn't sound like it should be an option for usb media. I think I'd prefer "Eject" for CD/DVD/BluRay, and "Safely Remove" for other usb media. And a separate option of "Unmount" for any file system so that you can unmount just one filesystem on a device if you want to.

I don't see the need for both "Eject" and "Safely Remove" - if you know why they're both there, let me know. Otherwise I might get around to raising it as a bug / enhancement. Although if something's going to be fixed, I'd much rather we got rid of tearing in vdpau on nvidia with composite enabled... ;o)

---

### Post by efflandt on 2010-01-27
You would use Unmount if you wanted to sync and umount a partition to modify the partition like with fdisk [or gparted would show a key (locked) on a mounted partition].

As mentioned Safely Remove would sync, umount all partitions and power it down.

Whatever you do, make sure that a USB storage is sync'd before you remove it, which I believe Ubuntu does within about 3 seconds after last write unless you change that.  So usually hot unplugging a device after a few seconds is not an issue as long as something is not still writing to it.  But better to be safe than sorry.

---

### Post by rossmoore on 2010-01-27
Thanks, Efflandt. I think all the contributors to this thread so far understand the importance of unmounting before unplugging. We also get the usefulness of unmount, to allow you to unmount but not power down the device.
The question now is "what is the difference between Unmount, Eject and Safely Remove"? All 3 are sometimes offered as options, but it's not clear that the last 2 represent different functionality for USB storage.

---

