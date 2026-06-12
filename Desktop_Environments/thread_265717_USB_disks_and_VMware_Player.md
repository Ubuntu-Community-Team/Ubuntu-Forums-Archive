---
title: "USB disks and VMware Player"
date: 2006-09-26
forum: Desktop Environments
---

### Post by scrook on 2006-09-26
I recently installed VMware player on Dapper and I noticed that whenever I activate a USB device on the guest OS, it is no longer accessable from ubuntu even if I unmount it from the guest.

For instance, when I mount my pen drive on the guest, the icon on my desktop disappears and the drive is no longer listed under /media. When I unmount the drive on the guest it doesn't come back on my ubuntu desktop.

From my understanding, for the guest to access the drive it has to be mounted on the host the whole time. Where I'm running into a problem is when I want to remove my drive I can't unmount it on ubuntu first so I have no other choice than to physically disconnect the drive.

Is there a way to get the drive to show up again on my ubuntu desktop without yanking it out and plugging it back in?

---

### Post by FrankVdb on 2006-11-06
I don't think there is a way...

The problem is similar the other way around: for the guest OS to see the USB device, the device must first be mounted by Ubuntu. However, as soon as you choose VM>Removable Devices>USB Devices> <yourdevice>, the guest Windows OS takes over "possession" of the USB connection, resulting in an unsafe removal on the host side. 

There is no way to solve this other than VMware to change their software. They should provide something that gives the connection back at unmount (from host to guest or from guest to host, whichever OS is unmounting).

Hope you understand what I mean.

---

