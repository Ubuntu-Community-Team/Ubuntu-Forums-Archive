---
title: "&quot;Users &amp; Groups &gt; User Privileges&quot; and /dev/modem Permissions"
date: 2005-05-17
forum: Desktop Environments
---

### Post by Slade Winstone on 2005-05-17
Hi,

I've recently installed a binary driver for a Copnexant HSF LinModem.  The modem is working fine.  However, whenever I re-boot Ubuntu the devices /dev/ttySHSF0 and /dev/modem only allow root access and prevent user access, so I have to "sudo chmod ... " to use the modem.

My user account is set to "Connect to Internet through modem devices" (from Users & Groups > User Permissions), but I can't access /dev/modem without changing the permissions manually.

Can anybody tell me how the User Permissions "Connect to Internet through modem devices" should be setting permissions to /dev/modem?  What entries are being set or what scripts are being run here?  How could I add an entries for the /dev/ttySHSF0 and /dev/modem to set the correct permissions when I check the appropriate entry in User Permissions?

Thanks,
Slade.

---

