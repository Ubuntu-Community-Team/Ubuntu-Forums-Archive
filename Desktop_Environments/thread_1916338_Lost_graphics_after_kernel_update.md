---
title: "Lost graphics after kernel update"
date: 2012-01-27
forum: Desktop Environments
---

### Post by UltimateCat on 2012-01-27
After a recent install of updates to my 2.6. 32-38 kernel; Ubuntu: Ultimate Ed 2.7
I restored all of my graphics I lost.

It became so complex I had to seek assistance from a Senior Member at Linux.

The solution was a command:
```
sudo cp /etc/X11/xorg.conf-backup-xxxxxxxxxxxx/etc/X11/xorg.conf

```

Until the command and a reboot was done; the Cattalyst Control Center continued to say that the driver was not installed when indeed it was. 

Also; going to the Appearance Preferences and clicking on desired effects; of course making adjustments in Compiz Fusion as well. 

I hope that in the future other members updates to their kernels won't be  effected graphically and have inoperative driver issues.  This was a real nightmare for me. 

I would be willing to work with  forum members at this as this ( members update their OS and have issues ( blank screen) and the lost of  graphics.

Life is challenging enough....having a working operating system shouldn't be such a hair raising experience.

  It's worth a lot to me for my OS to function properly and to help others who have suffered as I have.

Sincerely,
UltimateCat

---

### Post by dtbulmer2 on 2012-08-27
this happened to me!  Thanks for the code.

---

