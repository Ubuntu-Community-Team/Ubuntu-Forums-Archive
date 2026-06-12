---
title: "Home partition possibly corrupted (not mounting)"
date: 2011-05-08
forum: Desktop Environments
---

### Post by Enigmatic on 2011-05-08
I've had no problems with 11.04 until today, when I could no longer boot (waiting for /home, or the "serious errors on /home" errors). I see the partition in fdisk, but I'm not sure how to try and repair it, since I'm pretty certain I used the homedir encryption option when installing Ubuntu. 

Running file -sL /dev/sda5 shows "data", whereas all other partitions show a proper partition type. I am running all the latest updates. I did try e2fsck -b 8193 which was suggested, but I am denied saying the device is busy or mounted (yet it should not be mounted).

Any way of getting out of this without a reinstall? I'm traveling at the moment with no other laptop backup, which makes this even more inconvenient.

---

