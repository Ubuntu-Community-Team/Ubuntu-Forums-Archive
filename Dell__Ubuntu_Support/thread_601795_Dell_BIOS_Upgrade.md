---
title: "Dell BIOS Upgrade"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by mpgarate on 2007-11-03
following [this guide]("http://linux.dell.com/wiki/index.php/Tech/libsmbios"),an official guide from dell explaining how to upgrade the BIOS on dell machines, Everything went swimmingly until the final step, which gave me

> mike@mike-desktop:~/Desktop$ sudo dellBiosUpdate -u -f ./bios.hdr 

An Error occurred. The Error message is: 
    Programmer error: attempt to dereference a Null iterator.

Problem updating BIOS. Common problems are:

    -- Insufficient permissions to perform operation.
       Try running as a more privileged account.
          Linux  : run as 'root' user
          Windows: run as 'administrator' user

    -- dell_rbu device driver not loaded.
       Try loading the dell_rbu driver
          Linux  : insmod dell_rbu
          Windows: dell_rbu driver not yet available.

mike@mike-desktop:~/Desktop$ 



I have an open-source desktop (Dimension E521) shipped with freedos, running ubuntu gutsy
can anyone shed some light on my problem?

---

### Post by Linicks on 2007-11-04
Ummm.  I wonder if the module 'dell_rbu' does not load due to incompatiblity with the new kernel in Gutsy.

That would explain the 'Programmer error: attempt to dereference a Null iterator.'

I would mail a message off to the dell laptop mailing lists, get their attention on this.

Nick

---

### Post by MarilenCorciovei on 2007-12-08
Hello,

I was able to upgrade my bios on a D820 following [these steps]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/bios-upgrade-with-no-windows-or-floppy/view")

---

### Post by firebush on 2008-06-12
> **MarilenCorciovei said:**
> Hello,

I was able to upgrade my bios on a D820 following [these steps]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/bios-upgrade-with-no-windows-or-floppy/view")

Thanks, this worked.

---

### Post by Just Pete on 2008-06-26
Better solution, found by following links from here: [http://linux.dell.com/wiki/index.php/Products/Consumer](http://linux.dell.com/wiki/index.php/Products/Consumer)

(link for firmware upgrade is at the bottom - direct link: [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware) )

Instructions in a nutshell:

# set up repos
wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash
aptitude install firmware-addon-dell
aptitude install $(bootstrap_firmware -a)
update_firmware

This has the added bonus of finding firmware updates via the update manager!

---

