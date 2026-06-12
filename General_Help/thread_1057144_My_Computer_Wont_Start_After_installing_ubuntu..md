---
title: "My Computer Wont Start After installing ubuntu."
date: 2009-02-01
forum: General Help
---

### Post by emory on 2009-02-01
I just bought a brand new computer for $1000 and decided to try ubuntu on it. I loaded the disk and ubuntu came up just fine and all my stuff was there and everything worked. When i clicked the install button on the desktop it worked fine and installed fine. it told me to restart my computer to start useing ubuntu. When i restarted all that happened was the message came up on the screen, "No Operating System Found."
I tried making my slave hard drive the master hard drive and i got this message, "GRUB loading stage1.5

               GRUB loading, please wait....
               Error 21                         "
Please help!

---

### Post by Crafty Kisses on 2009-02-01
A couple of questions here, does this computer also have a copy of Windows on it? That error usually comes up if your BIOS cannot recognize the disk. I say if you have a Windows XP/Vista recovery disk, you can run the following:
```
FIXMBR
```
Then reboot back into Windows, and check for any errors.

---

### Post by emory on 2009-02-01
Before i installed ubuntu my computer had windows vista on it. Also i cannot enter the bios to change my boot options or anything.

---

### Post by emory on 2009-02-01
I dont have any recovery disks either because vista merely came on my computer.

---

