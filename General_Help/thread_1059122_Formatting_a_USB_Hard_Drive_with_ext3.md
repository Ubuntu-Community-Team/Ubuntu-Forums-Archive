---
title: "Formatting a USB Hard Drive with ext3"
date: 2009-02-03
forum: General Help
---

### Post by KillaW0lf04 on 2009-02-03
Hey guys, so i just got a new 250gb USB hard drive and im attempting to format it in ext3 using gparted, but everytime it completes the format and i try copying something into the drive it tells me "Error opening file '/media/disk-1/Video.ogv': Permission denied" for example. 

Is there something im forgetting to do during the format? Do i have to set permissions before i format it? When i formatted it with FAT32 it worked fine but id prefer not to use this because of all the drawbacks its known for. 

Thanks in advance for any help

---

### Post by taurus on 2009-02-03
You need to change the ownership of the mount point for that drive, /media/disk-1, from root to your login name.  Then, you can write to it anytime you want.  Assuming your login name is wolf, you would run something like these in a terminal.

```
sudo chown -R wolf:wolf /media/disk-1
ls -la /media
```

---

### Post by Sumogrind on 2009-02-11
Thanks, that worked perfectly for me.

---

### Post by schpunty on 2009-02-22
Worked excellent!
Thanks a bunch!

---

