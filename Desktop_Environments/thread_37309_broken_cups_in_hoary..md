---
title: "broken cups in hoary."
date: 2005-05-26
forum: Desktop Environments
---

### Post by oscarh on 2005-05-26
hi!

i have problems with cups not working at all.
what happends is that cups does start, and all looks good.
but when i try to connect to cupsd, the server does not respond.

if i try and restart cups using:
sudo /etc/init.d/cupsys restart
it says:
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!

i have removed and purged cupsys, cupsys-driver-* and reinstalled. the problem remains. i am using hoary repositories and installed hoary stable from the cd. i have run apt-get update and apt-get dist-upgrade.

in the error log i find this:
I [26/May/2005:23:22:38 +0200] Listening to 7f000001:631
I [26/May/2005:23:22:38 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [26/May/2005:23:22:38 +0200] Configured for up to 100 clients.
I [26/May/2005:23:22:38 +0200] Allowing up to 100 client connections per host.
I [26/May/2005:23:22:38 +0200] Full reload is required.
I [26/May/2005:23:22:38 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [26/May/2005:23:22:38 +0200] LoadPPDs: No new or changed PPDs...
I [26/May/2005:23:22:38 +0200] Full reload complete.
E [26/May/2005:23:22:38 +0200] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.


cheers

---

### Post by oscarh on 2005-05-27
[QUOTE=oscarh]hi!

i have problems with cups not working at all.
what happends is that cups does start, and all looks good.
but when i try to connect to cupsd, the server does not respond.

if i try and restart cups using:
sudo /etc/init.d/cupsys restart
it says:
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!

i have removed and purged cupsys, cupsys-driver-* and reinstalled. the problem remains. i am using hoary repositories and installed hoary stable from the cd. i have run apt-get update and apt-get dist-upgrade.

in the error log i find this:
I [26/May/2005:23:22:38 +0200] Listening to 7f000001:631
I [26/May/2005:23:22:38 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [26/May/2005:23:22:38 +0200] Configured for up to 100 clients.
I [26/May/2005:23:22:38 +0200] Allowing up to 100 client connections per host.
I [26/May/2005:23:22:38 +0200] Full reload is required.
I [26/May/2005:23:22:38 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [26/May/2005:23:22:38 +0200] LoadPPDs: No new or changed PPDs...
I [26/May/2005:23:22:38 +0200] Full reload complete.
E [26/May/2005:23:22:38 +0200] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.


cheers[/QUOTE]
 the issue has been resolved.
i don't know what the fix was really,
but removing purging,
reinstalling AND rebooting three times....
printing works and i'm a happy camper again.

still hate it when it can't be resolved by hand :(

---

