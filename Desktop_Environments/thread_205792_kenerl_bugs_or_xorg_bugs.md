---
title: "kenerl bugs or xorg bugs??"
date: 2006-06-29
forum: Desktop Environments
---

### Post by zjcim on 2006-06-29
i dowload the ubuntu dapper and xubuntu dapper
burned them cdrom
but i got system freeze after i install the system in the harddisk,just "dead",keyborad and mounse both no response

Then i try the xubuntu ,same problems,espeically when i max maximize ro minimize a window,

IBM laptop x24 p3-m 1.13 ati 8m 384 sdram 40g hd

After a long time desperation,i try the Debian/stable (2.6.8-2kernel + xfree6.8
) it is ok ,never  freeze again.
But after i updated the dist to the Debian/testing (2.6.15-1kernel + xorg) i got phenomenons just like above :system dead thoroughly
but something changed ,system will not die when maximizing or minimizing window,just after sometimes of running ,itself goes dead

first i think may it's a bug of kernel :not support acpi or fan speed well
then i build a kernel with cpu scailing support 2.6.16-20
still "system freeze problems" there is

---

