---
title: "Display scaling changes when external monitor detached on boot 20.04"
date: 2020-08-22
forum: Desktop Environments
---

### Post by heluca on 2020-08-22
My machine has a HiDPI display and an external monitor that isn't HiDPI so I've set a different scale factor for each.  However the display scaling isn't correct when I boot without the external monitor.  The behaviour is a bit odd:

Built in display set to 200%, External monitor is set to 100%.  Good.

I boot the machine without the external monitor: built in display is 100%.  Argh!

I connect the external monitor: built in display switches to 200% and external is 100%.  Good

I disconnect the external monitor: built in display stays at 200%. Good

I reboot without the external display and the scaling factor is 100%.  Argh!

I set the scale to 200%.  Good

I reboot without the external display and the scaling factor is 100%.  Argh!

It looks like a bug, but can someone explain how Ubuntu chooses the scaling factor?  
On desktop login, can I set a workaround to force the primary display to 200%?  I only know how to do this from the display settings GUI.

Thank you!

---

