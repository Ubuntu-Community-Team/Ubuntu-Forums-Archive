---
title: "Memory limit in Ubuntu on Poweredge?"
date: 2008-01-25
forum: Desktop Environments
---

### Post by mwob on 2008-01-25
Hi,

We have a Dell Poweredge 2650 server that we are using to host virtual machines with VMWare Server. When we installed Ubuntu (Gutsy Desktop 32bit) the machine had 3gb of ram.

We then bought 4 gig (2x2gb) for the machine, so it now has 7gb (2x1gb, 2x512Mb, 2x2gb). When the machine is turned on the bios says it has 7gb, so thats OK, but when Ubuntu loads, it says I have just 3.7Gb in there. (I checked this with the "System Settings" and also with the "top" command).

Is there something I need to do with Ubuntu to help it see the memory, or is this a problem with the Server? In the BIOS I can't see anything relevant, redundant memory is disabled. The BIOS version by the way is A28, but I don't think that I need to update the BIOS because it recognises that I have 7GB in there.

Thanks guys!

Matt.

---

### Post by elleipein on 2008-01-25
You will need 64 bit to see the extra memory. 32bit can only see around 4gb while 64bit has a theoretical limit of 16 exbibytes ( 16 billion gb)

---

### Post by mwob on 2008-01-28
Umm, Ok, I'm not sure what you mean. 

I don't think that the PowerEdge is a 64bit core PC, but it does support up to 12Gig of ram. It has Physical Address Extensions I think to allow it to do this. But, if I try to install the 64bit version of Ubuntu, will it work on that server??

Help!

---

### Post by elleipein on 2008-01-28
There should be not issue going from 32bit to 64bit. I would recommend doing a full back up. But the 4gb limit is not a limit set but any OS it is an actual limit of 32bit OS's in general. 

This link should give you all the information you need about 32bit and 64bit [http://en.wikipedia.org/wiki/64-bit]("http://en.wikipedia.org/wiki/64-bit")

---

