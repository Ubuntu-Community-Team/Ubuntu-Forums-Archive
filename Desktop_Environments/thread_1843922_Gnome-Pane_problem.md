---
title: "Gnome-Pane problem"
date: 2011-09-14
forum: Desktop Environments
---

### Post by raunhar on 2011-09-14
Ubuntu 10.10

For the past few days, I am facing this problem:
Many times, when I start my laptop the panel doesnot load properly. Most of the time, The Network icon does not appear full. As a result, clicking on icons start some other function. For ed, if I click on Evolution icon, it will show up calender. Battery will display sound control.

On giving the command
gconftool --recursive-unset /apps/panel && killall gnome-panel
 the panel shows up full with no problems.

On reboot, it is back to square one.
The screen shot is attached.
When this happens, the clock also stops working.

---

