---
title: "&quot;Detect Displays&quot; does not work"
date: 2008-12-15
forum: General Help
---

### Post by bsmith1051 on 2008-12-15
I have my Ubuntu 8.10 system setup on a KVM switch.  If I bootup the system while the switch is 'on' the other computer then the monitor EDID info is wrong (e.g. available resolutions).  This is predictable and, in theory, my KVM should do a better job of passing-through the EDID request.  But even so I should just be able to click the 'Detect Displays' button (in System > Preferences > Screen Resolution) and fix it, but the button doesn't seem to do _anything_?

P.S. I am running the proprietary Nvidia driver v177.80 (per the Ubuntu Hardware Drivers suggestion).  The 'Detect Displays' button doesn't work there either.

---

### Post by havencruise on 2008-12-15
Are you sure that the driver is enabled and running? In System>Administration>Hardware drivers, that driver must have the status "In Use".

---

### Post by nikgare on 2008-12-15
To get your system to notice the monitor correctly, just reboot X.

---

