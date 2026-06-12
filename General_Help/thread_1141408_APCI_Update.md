---
title: "APCI Update"
date: 2009-04-28
forum: General Help
---

### Post by ftabor on 2009-04-28
I need a little help here.  In todays update I think there was an update to ACPI.  I think it has broken my boot/shutdown process.

I have an HP Pavillion dv6000 laptop with dual core amd64 cpus.  With Intrepid in order to boot up, I had to constantly press the enter key, or hold it to get it too boot.  In the known bugs for Intrepid I found this was an know bug.  A little later I found a work-around was to add APCI=noirq to the end of the kernel line to get it to boot.

Upgraded to Jaunty 9.04 and all was well.  Box booted just fine with no edits to Grub and everything was just lovely.

So today, I installed updates from the update manager and now not only will it not boot without holding the enter key, it won't shut down without holding the enter key.  Adding APCI=NOIRQ to the kernel line doesn't work.  

So I have two questions.  How do I determine what updates were applied?  I think there was an update to APCI.  And how do I undo that update, short of reinstalling fresh from the live CD?

Thanks for any help.

Additional information.  This problem is occurring on battery power only, in 9.04.  On A/C power it boots and shuts down fine.  In Intrepid it didn't matter if it was on battery or not.

---

