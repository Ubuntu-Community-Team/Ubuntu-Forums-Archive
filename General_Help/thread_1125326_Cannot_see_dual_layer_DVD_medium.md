---
title: "Cannot see dual layer DVD medium"
date: 2009-04-14
forum: General Help
---

### Post by imbjr on 2009-04-14
According to K3B and Imgburn under WINE, I should have the ability to burn DVD+R DL disks. hal-device also reports storage.cdrom.dvdplusrdl = true  (bool).

But I try putting a Verbatim disk in my DVD+-RW GSA-H31N drive and ... nothing.

ImgBurn eventually reports "Medium Not present". It seems I cannot even get to the point where a burn option is present in the many different burn tools I've looked at.

The drive would appear to be otherwise OK as a DVD+RW is easily handled.

Is this just the particular brand of disk not being usable? Or am I missing an important detail?

---

### Post by timcredible on 2009-04-14
what does k3b say?

---

### Post by imbjr on 2009-04-14
> **timcredible said:**
> what does k3b say?

That the device can handle the format.

It shows a dialog with various formats and the appropriate one for DVD+R DL is supported. But so does ImgBurn and the hal-device list say this.

Now, as far as I know, I don't need to do any special mounting and when I've tried I get the "no medium" message, so at this stage I have to assume that the disks are duff, or the device is lying about what it will support.

---

