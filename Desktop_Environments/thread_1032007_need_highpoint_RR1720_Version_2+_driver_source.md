---
title: "need highpoint RR1720 Version 2+ driver source"
date: 2009-01-05
forum: Desktop Environments
---

### Post by jamesgate on 2009-01-05
The Highpoint open source driver link for the RR1720 SATA Controller downloads the model RR1740 source.  After successful "make install" modprobe fails:
"FATAL: Error inserting rr174x (/lib/modules/2.6.24-21-generic/kernel/drivers/scsi/rr174x/rr174x.ko): No such device"

Am I correct that this tells me the "rr174x.ko" module is not the correct module for an RR1720 Controller, and I really do need the RR1720 source code?

I found a Version 1.0 source for rr172x on a forum but this version does not compile with linux-headers-2.6.24-21-generic, it's too old.  "V1.0" suggests there should be a V2.X.  I posted to Highpoint but no response yet.

Does anyone have a Version 2+ link for the RR1720 open source driver?

thanks -

---

### Post by Corsari on 2009-01-07
Dear James,
RR1740 is a different card... and @ highpoint they didn't fixed the link.

But let's check this out 
[http://www.highpoint-tech.com/BIOS_Driver/](http://www.highpoint-tech.com/BIOS_Driver/)

you'll see that RR172x is still available.

Navigating through that path you'll land in this directory
[http://www.highpoint-tech.com/BIOS_Driver/rr172x/Linux/](http://www.highpoint-tech.com/BIOS_Driver/rr172x/Linux/)

which has also got the generic drivers.

Now, if you succeed in compiling the module, please help me in compiling the Debian version. (Sorry, I'm not strong with drivers / modules compile, and so I don't know how to succesfully compile them. I tried but I get an error 2 from the compiling process)

Thank you if any Debian module or compile process comes as answer and help to me.

Ciao
Robert

---

