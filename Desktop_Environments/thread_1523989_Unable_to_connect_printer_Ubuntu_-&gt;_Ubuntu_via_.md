---
title: "Unable to connect printer Ubuntu -&gt; Ubuntu via network"
date: 2010-07-04
forum: Desktop Environments
---

### Post by muddysmind on 2010-07-04
Ok, I give up.. after an hour trying to get my HP 7600 to network connect I'm asking for help finally.

My main box is usb connected to my HP Photosmart 7600 and works fine, my daughter has her winxp box connected to it over network as well.
My wife's Ubuntu box (same OS and version as mine 9.10) CANNOT connect in any way, shape or form. I've tried every protocal, port, helper program (hp-setup, cups local webpage etc..) and nothing.
I have the printer shared.


Any ideas why connecting to a network printer in the same OS and version would take so much work?

Also we're all on the same network, & subnet with no filtering or firewalling in between the boxes.

Any advice or assistance would be so very very welcome and appreciated.

-Muddy


*resolved* After trying everything else I restarted cups on the box the printer is attached and everything mysteriously works.

---

### Post by Morbius1 on 2010-07-04
Is the printer both shared and published?

_Enable  Sharing for that Printer._
Administration > Printing >  Right Click the attached printer > Properties > Policies
Check  Enabled, Accepting Jobs, and Shared

_ Enable Publishing of  the Shared Printer_
Administration > Printing >  Server > Settings > Check "Publish Shared Printers connected to  this system"

If all that is set and it still can't find it by browsing then try to access it directly:

Administration > Printing > New > "Other"

In the "Enter URI" box enter one of the following formats:

ipp://WORKGROUP_NAME/MACHINE_NAME:631/printers/Linux-Printer-Name[FONT=monospace]
[/FONT]ipp://MACHINE_NAME:631/printers/Linux-Printer-Name
ipp://192.168.0.100:631/printers/Linux-Printer-Name

---

