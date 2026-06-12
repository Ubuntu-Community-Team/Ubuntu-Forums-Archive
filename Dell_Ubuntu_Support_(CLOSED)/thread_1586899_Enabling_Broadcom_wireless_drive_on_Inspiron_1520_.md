---
title: "Enabling Broadcom wireless drive on Inspiron 1520 disables eth0"
date: 2010-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Raisor on 2010-10-02
I just installed Ubuntu 10.04 LTS on my Dell Inspiron 1520 and everything works fine.  I went to System -> Administration -> Hardware Drivers and installed the Broadcom STA wireless driver and then rebooted.  As soon as I reboot, I can no longer connect using my wired connection which was known as eth0.  It is no where to be found on the system.  As soon as I uninstall the wireless driver and reboot, the eth0 is back and working.  

Is this working as designed or is this a problem?  If it is a problem, how do I fix it?  I have tried searching here and on google but I was unsuccessful in finding any information regarding it.  

Running lspci says that my ethernet card is a Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) and that my wireless card is a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03).

Please let me know if I can provide more information to assist in fixing this.

[Edit] This issue appears to have resolved itself.  All I did was remove the wireless driver, shutdown my computer, started it up again today without an Ethernet cable plugged in, installed the wireless driver and rebooted.  Now my computer sees both the ethernet and the wireless connections.  Very odd...

---

