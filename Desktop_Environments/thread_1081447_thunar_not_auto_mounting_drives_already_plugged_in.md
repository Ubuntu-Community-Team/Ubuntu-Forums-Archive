---
title: "thunar not auto mounting drives already plugged in at reboot"
date: 2009-02-26
forum: Desktop Environments
---

### Post by justinsmith2009 on 2009-02-26
Using Hardy 8.04.2. 

I am trying Thunar to automatically mount USB drives after reboot. It shows me an icon for the drive on desktop and only mounts it when I click on it. I want it to automatically mount the drives. 

Tried many options which all work, but looking for better solution:

Tried rmmod and modprobe usb-storage which detects the drives and mounts them, but will be an issue if I want to boot from USB Drive. 

Tried ivman, and after booting I do an /etc/init.d/ivman restart, and it mounts the drive - but doesn't use disk labels. 

Tried using thunar-vollman --device-added, but the output of lshal is too complicated for me to understand. 

Please help ........

---

### Post by patv on 2009-02-27
Experiencing same problem as OP with Intrepid xu. Any suggestions most welcome.

---

