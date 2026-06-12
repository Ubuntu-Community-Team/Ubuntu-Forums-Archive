---
title: "A hard disk vanishes when a second disk is added. (eSATA box)"
date: 2012-02-08
forum: Desktop Environments
---

### Post by nekatreven on 2012-02-08
I have an EeeBox EB1501 that I am having an eSATA storage issue with. As best I can tell this is the correct place to post this, but I apologize if not.

This computer/nettop is running Ubuntu 10.04.3 Desktop (x86) with a full GUI (but I am usually off-site and use ssh access only). While the EB1501 has an eSATA port I've never been able to get it to handle a port multiplier, and so I have an Addonics ADU3ESA USB2/3 to eSATA adapter plugged in, which connects to a Rosewill RSV-S5 eSATA port multiplier/5-bay storage enclosure.

The problem I have is that while up to five 1.5TB disks will work fine, I can only put one 3TB drive in the storage enclosure at a time. When I add a second 3TB disk, both of them disappear (but any other disks that are in the enclosure are still visible).

I have not been able to get a ton of help out of Rosewill on their enclosure, and although Addonic's adapter support turned out to be pretty impressive, they don't seem to have the answer to this one.

Does anyone have any guidance on how I can begin to troubleshoot this?

There is one known issue that occurs when mixing this adapter with the Sil3726 port multiplier that is in my storage enclosure, which is that an extra (non-existent) disk shows up in /dev/. I am working on hiding this extra device with a udev rule, but I suspect my issue with the larger drives is a separate one altogether.

TIA for any insight,
Mark

---

