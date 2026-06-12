---
title: "How do I automatically activate Hardware drivers on start-up ?"
date: 2009-04-30
forum: General Help
---

### Post by paddyboy on 2009-04-30
Hi, Recently installed 9.04 and fixed most issues with Wireless. However, I would like a little bit of code to automatically activate my wireless driver (System>Admin>Hardware Drivers>Broadcom STA wireless driver) and not ask for authorisation etc. Thanks.

---

### Post by mb_webguy on 2009-04-30
> **paddyboy said:**
> Hi, Recently installed 9.04 and fixed most issues with Wireless. However, I would like a little bit of code to automatically activate my wireless driver (System>Admin>Hardware Drivers>Broadcom STA wireless driver) and not ask for authorisation etc. Thanks.

You shouldn't have to activate proprietary drivers every time you reboot.

Fortunately for you, I've had the same issue you're encountering with the STA driver.  Hardware Drivers isn't automatically blacklisting certain conflicting modules, preventing the STA driver from being added at startup.  If your wireless card has a hardware switch, you might be able to fix this with minimal effort.  Turn off your wireless card with the switch.  Now reboot your computer.  After you've logged back in, turn the card back on using the switch, and activate the driver using Hardware Drivers.  Now reboot again.  Your wireless card should start up with no problems.

If your wireless card doesn't have a hardware switch, you'll have to track down the conflicting modules and add them to the /etc/modprobe.d/blacklist.conf file.  My guess would be that wl, ssb, b43, and/or b44 might be the culprit(s).

---

### Post by paddyboy on 2009-05-01
Thanks for that webguy, looking through the syslog it does indeed seem to be the "wl" module (at least searching for the others picked up nothing). So can I simply add something like this ? ...

# replaced by b43 and ssb.
blacklist bcm43xx
**blacklist wl**

Then reboot I guess. 

P.S. The hardware switch/light was the cause of all my woes in the first place...when the light was on the card was off, when the light was off the card was on. But I know that now, and don't need to chase it down.

---

