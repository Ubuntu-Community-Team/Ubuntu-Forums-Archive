---
title: "Bios Update for Dell Studio 1450"
date: 2010-12-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madhums on 2010-12-18
Has anyone successfully updated Dell Studio 1450 BIOS to the latest version (A05) ?

I followed [http://linux.dell.***/wiki/index.php/Tech/libsmbios_dellBiosUpdate]("http://linux.dell.***/wiki/index.php/Tech/libsmbios_dellBiosUpdate")

# getSystemId resulted in

Libsmbios version:      2.2.13
Product Name:           Studio 1450
Vendor:                 Dell Inc.
BIOS Version:           **A01**
System ID:              **0x02E8**

I cannot find the above versions in [http://linux.dell.***/repo/firmware/bios-hdrs/]("http://linux.dell.***/repo/firmware/bios-hdrs/")


I tried the other option as well as listed here [http://linux.dell.***/wiki/index.php/Repository/firmware#Putting_it_all_together]("http://linux.dell.***/wiki/index.php/Repository/firmware#Putting_it_all_together")

$ wget -q -O - [http://linux.dell.***/repo/firmware/bootstrap.cgi](http://linux.dell.***/repo/firmware/bootstrap.cgi) > bootstrap.sh
$ sudo  bash bootstrap.sh
$ sudo aptitude install firmware-addon-dell
$ sudo aptitude install $(sudo bootstrap_firmware -a)
$ sudo update_firmware

Even this couldn't find any new updates! 

The latest BIOS version for dell studio 1450 is A05. 

Any help ?

---

