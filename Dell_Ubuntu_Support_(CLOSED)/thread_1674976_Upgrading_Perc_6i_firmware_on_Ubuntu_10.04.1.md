---
title: "Upgrading Perc 6/i firmware on Ubuntu 10.04.1"
date: 2011-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeera on 2011-01-24
Hi there,

I’ve got OMSA 6.4 working well on a PowerEdge R410 – all hardware is seen and reporting fine. However, I’m having issues upgrading the Perc 6/I firmware though. I followed instructions here: [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware). Running update_firmware only detects the system BIOS, not the Perc 6/I at all. When I run aptitude install $(bootstrap_firmware -a)I get a bunch of errors saying it couldn’t find any package whose name or description matched various pci devices. 

Part of the instructions mentioned setting up the system for Dell-community. However, when I run wget -q -O - [http://linux.dell.com/repo/community/bootstrap.cgi](http://linux.dell.com/repo/community/bootstrap.cgi) | bash, it tells me that it’s unable to determine that I’m running an OS I know about.

Am I missing something? Any suggestions would be much appreciated.


Thank you,
Jeera

---

