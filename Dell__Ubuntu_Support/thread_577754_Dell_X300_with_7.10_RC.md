---
title: "Dell X300 with 7.10 RC"
date: 2007-10-16
forum: Dell  Ubuntu Support
---

### Post by carac on 2007-10-16
Just posting after spending a few hours with the latest RC (kernel 2.6.22-14).

Pretty much everything works OK (including compiz) with 2-3 exceptions:

- bcm43xx is broken for Dell Wireless 1400 Mini-PCI (Broadcom 4324 I believe)  - seems to be so in all recent 2.6.22 distributions :(
(I have placed a more detailed update of a rather old post in the bug list on the launchpad)

- with bcm43xx also it seems that RESUME (after SUSPEND or HIBERNATE) does not work; however after blacklisting bcm43xx and installing ndiswrapper both the network - including WPA - and resume seem to work !

- the only exception seems to be if suspend is called on closing the lid - with that SUSPEND does not work !!! However, I repeat - it works perfectly when called from different applets on the top panel; IS IT POSSIBLE THAT THE APPLETS ARE CALLING A DIFFERENT SCRIPT THAN THE ONE CALLED ON LID CLOSE ?

Overall very usable :) (except that small final problem which seems to be just the wrong script or something - please let me know if there is a simple fix for it).

---

### Post by neptho on 2007-10-16
> **carac said:**
> Just posting after spending a few hours with the latest RC (kernel 2.6.22-14).


 the only exception seems to be if suspend is called on closing the lid - with that SUSPEND does not work !!! However, I repeat - it works perfectly when called from different applets on the top panel; IS IT POSSIBLE THAT THE APPLETS ARE CALLING A DIFFERENT SCRIPT THAN THE ONE CALLED ON LID CLOSE ?

Lid close by default executes /etc/acpi/lid.sh.

---

