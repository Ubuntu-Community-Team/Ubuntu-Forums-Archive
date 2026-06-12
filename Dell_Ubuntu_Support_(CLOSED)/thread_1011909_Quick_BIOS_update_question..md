---
title: "Quick BIOS update question."
date: 2008-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by unoodles on 2008-12-15
Ok, I am going to update my bios using this page:
[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

My quick question:
The page says to download the file name system_bios_ven_0x1028_dev_SYSTEM_ID_version_BIOS_VERSION.
Should BIOS_VERSION be the version that shows up with the getsystemid command? or should I get the highest numbered version?

---

### Post by shae on 2008-12-15
SYSTEM_ID should be the system id you get from that earlier command.  The BIOS_VERSION should be the version you want to update to, usually the highest.

---

