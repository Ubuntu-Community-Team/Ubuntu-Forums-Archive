---
title: "Cups multiple queues, one printer."
date: 2009-03-05
forum: General Help
---

### Post by sigmason on 2009-03-05
I have Windows clients printing to Ubuntu cups servers running Ubuntu 8.10.  The Windows XP Service Pack 2 clients don't like the raw queue that cups sets up.  If they print to it the stuff comes out but the requests to change tray are ignored.  Oddly, if I update those same Windows XP computers to Service Pack 3, the tray requests work fine.  So to handle both I created to queues that service the same printer.  The one for Service Pack 3 is raw, the one for Service Pack 2 has a PPD.

Both queues work, but if jobs end up in both queues at the same time, it ends up trying to go out the port at the same time.  In short both queues empty into the device at the same time and literally mix together.  There does not seem to be any fix for this.  I could run a System V script on the raw queue to hold it back, but that would only work for a raw queue in cups.  Worse that would seemingly create a priority structure that seems both backward and secondary to the cups print priority structure.

For now I've fed the filtered queue to the raw queue via localhost and IPP printing.  This gets the jobs into the proper prioritized holding pattern in the raw queue, while allowing me to 'bake' them however I like before feeding the raw queue.  This makes the most sense from a print process perspective.  However, this means that I have effectively now 2 copies of the same print job, one in each queue.  The copy in the filtered queue and the copy in the raw queue, till the job clears.

Does anyone know of a better way to get multiple print queues to print to the same printer (therefore port) and keep the output streams from getting mixed together?

I would print everything to the PPD filtered queue, as both Windows XP Service Pack 2 and 3 could handle that.  However, that only seems to work for the Microsoft WHQL drivers for this printer (HP 4000 series) when the driver is PCL.  When the driver is postscript the PPD can't handle it and the job gets stuck in the queue.  Still even fixing the PPD would strike me as covering for the apparent fact that cups is not checking and seemingly cannot check the status of the port it is using when printing to a hardware device.  So anytime a set of queues points to the same physical hardware port it will not toggle between them it will mix the outputs together.

Sigmason

---

