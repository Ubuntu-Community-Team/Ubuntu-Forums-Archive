---
title: "Problem with mounting external HDD caused by Vista"
date: 2009-01-30
forum: General Help
---

### Post by markjs on 2009-01-30
I have a 500GB Seagate SATA external hard drive, and the trouble is, if I don't "safely remove" it in Vista, I can't mount it in ubuntu.  This in itself is not a problem, the problem is, that the ONLY way I can get Vista to even give me the option to "safely remove", is if I boot Vista with the drive plugged in and turned on.  That is not how I use the drive.  It's just backed up files that I only need on an occasional basis for safekeeping.  I prefer to leave it off all the time because it saves wear and tear, and I tend to forget to turn it off.  As it stands now, when I try to mount it in ubuntu, I have to plug it in, turn it on, get denied access, leave it on and plugged in, boot to Vista, use the safely remove option, turn it off, unplug it, then reboot to ubuntu, plug it in, turn it on again, then it works.  Quite and ordeal, but as far as I can tell Vista leaves me no other option?  Is there something I am missing?

---

### Post by taurus on 2009-01-30
If Ubuntu can't mount that drive, assuming it's /dev/sdb1, because it is not safely removed the last time you used it, you can use ntfsfix to fix it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix _/dev/sdb1_
```
Replace _/dev/sdb1_ with the right device.

---

### Post by markjs on 2009-01-30
OK, thank you, that is very helpful, but if anyone else knows of any way to shut the drive down in Vista when it will not give me the "safely remove" option on the right click menu, that would be helpful too?!?

---

