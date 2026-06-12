---
title: "Creating a restore DVD"
date: 2008-06-04
forum: Desktop Environments
---

### Post by uMuppet on 2008-06-04
I have created a custom Mythbuntu install, its taken me a while and several attempts to get everything working the way I want.  But now I want to clone my setup and send the copy to some friends who have the exact same hardware setup (but no PC knowledge) to install on their system.

Can I create a bootable DVD of my Mythbuntu OS so all I would have to do is boot the PC with the DVD in it and it will restore the system to what I have now?

---

### Post by mattress on 2008-06-05
The easiest way is to simply make a dd copy of the disk from a LiveCD. There is an external app to do this, but I never managed to get it working 100%

Just boot up from a LiveCD and mount a disk to copy the image to and run
```

dd if=/dev/whatever of=/mnt/yourbackupdisk/mythbackup.img

```

Then just reverse the process when you want to install..

m

---

