---
title: "Firefox and Evolution being launched on power events"
date: 2008-04-16
forum: Desktop Environments
---

### Post by vmark on 2008-04-16
As the title suggests, I am having a weird issue.

I have Ubuntu 7.10 installed on an EeePC (it was originally eeeXubuntu, but I installed ubuntu-desktop)

When I pull the power cord, in addition to all the regular power saving measures (screen dimming, tray popup), firefox gets launched.

When I re-insert the power cable, in addition to the screen resuming normal brightness, evolution is launched.

I can't find any mention of people having similar problems, and I can't find in my configuration anything that would cause this.

Any help appreciated as this is rather annoying.

Cheers,
Mark

---

### Post by vmark on 2008-04-16
Further experimentation has identified that it is actually running whatever is set as the default web browser and default mail reader respectively, not specifically just firefox and evolution.

---

### Post by vmark on 2008-04-16
More investigation shows that removing power sends hotkey event ATKD 00000051 0000000c and plugging it back in sends 00000050 0000000d, which map to webbtn.sh and mailbtn.sh respectively.

Any idea why these power events are triggering keyboard events?

---

### Post by vmark on 2008-04-16
Turns out asus_acpi may be sending extra events on the eeepc.

[http://forum.eeeuser.com/viewtopic.php?id=5563](http://forum.eeeuser.com/viewtopic.php?id=5563)

---

