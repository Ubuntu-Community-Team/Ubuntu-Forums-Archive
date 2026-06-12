---
title: "4 hard drives, which bios device has windows?"
date: 2009-05-31
forum: General Help
---

### Post by googlegot on 2009-05-31
I have 4 hard drives, and one of them has windows installed on it, and I'm trying to get grub to boot it.  Heres my setup:

IDE controller 1 master: 100 gig drive with windows (partition 1 is fat, partition 4 (do not ask why this is) is windows)
IDE controller 1 slave: CD drive

SATA 1+2: dmraid (fakeraid) with ubuntu
SATA 3: 160 gig drive for media storage

I cant for the life of me figure out what my bios has these drives listed as, and theres no device.map in my grub folder.

Any ideas?

---

### Post by Legace on 2009-05-31
Type in blkid in Terminal and post output.

---

### Post by googlegot on 2009-05-31
I just figured it out, going into the grub command line and typing "root (hd" then tabbing listed my hard drives, then I checked each one for their partition tables by typing "root (hdX," then tabbing, and in my setup, my windows partition is at (hd1,3).

Now if I could just figure out how to get it to boot...

---

### Post by philinux on 2009-05-31
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Might get you going.

If not google > grub windows stanza

---

