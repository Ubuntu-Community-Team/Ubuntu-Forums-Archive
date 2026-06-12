---
title: "Moving the Ubuntu Hard disk to a new pc"
date: 2009-04-07
forum: General Help
---

### Post by elliotn on 2009-04-07
Is it posible for me to move the harddisk that has ubuntu into a new pc without reinstalling and loosing all my updates etc.

---

### Post by frodon on 2009-04-07
Yes it is and should work quite well if your new hardware is linux friendly hardware. However in such case fresh install is always better, it is the occasion for a clean up and to get an even more stable install.

---

### Post by 3Miro on 2009-04-07
The only problem would be the hardware. The new computer has different hardware and therefore different drivers.

If the drivers are open source, the kernel will catch on them, the first time it will take some time to boot.

If the drivers are proprietary then you may have some trouble. My advice would be to remove all the proprietary drivers that you have installed from the Hardware Manager (System -> Admin -> HW Manager). You have to do the last one especially if the video is different. Make sure to know the right commands to reconfigure /etc/X11/xorg.conf if the computer doesn't boot into graphical mode. (I don't know the commands, sorry)

---

