---
title: "Strange X with an icon"
date: 2016-05-29
forum: Desktop Environments
---

### Post by zkab on 2016-05-29
I have Ubuntu 15.10 (64-bits) with Xfce desktop on a computer hooked to my LAN.
I made a link to a document on that Xfce computer, the document is stored at a NFS volume on a Ubuntu server.
The link was sent to desktop and when I click at the icon it works fine.
But after a reboot of the Xfce computer then the link icon has been provided with an X - but it works OK when clicking.
My question is - where does the X come from and why ?
Please check the attachment.

---

### Post by ajgreeny on 2016-05-29
Is the NFS volume mounted always or is it only mounted when you click on, for example, that icon?

I suspect that X is simply added because the system can not at that moment see the file it links to.
I do not know much about NFS filesystems, but perhaps if you make sure it is mounted at boot by adding a line to /etc/fstab the X will disappear.

---

### Post by zkab on 2016-05-30
The NFS volume is mounted with autofs ... it is mounted when it is used.
I agree with you that it could be the reason for X to appear.
But I guess it must be configurable in Xfce to avoid this X ... but I don't know how to do it.

---

### Post by ajgreeny on 2016-05-30
> **zkab said:**
> The NFS volume is mounted with autofs ... it is mounted when it is used.
I agree with you that it could be the reason for X to appear.
But I guess it must be configurable in Xfce to avoid this X ... but I don't know how to do it.
Nor me!
Sorry.

---

