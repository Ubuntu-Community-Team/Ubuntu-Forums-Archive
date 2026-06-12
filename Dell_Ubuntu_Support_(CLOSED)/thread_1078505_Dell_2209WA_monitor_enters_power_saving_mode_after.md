---
title: "Dell 2209WA monitor enters power saving mode after 3-4 minutes despite a signal :("
date: 2009-02-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kraymore on 2009-02-23
Dell 2209WA LCD monitor enters power saving mode on Intrepid despite there still being a signal and it cannot be disabled from the monitor settings.  i don't know what setting i can adjust, so that it wont enter this mode mode. it forces me to do a unsafe shutdown, until i can fix this.  Dell's response was 'call Ubuntu'.

[UPDATE:  The problem exists with the drivers bundled with the Restricted Driver manager, and the envyng package solution.  the ATI open source driver however, has no issues at all with dpms enabled, using gnome power management, and needs no extra terminal manipulation once you switch to those drivers]


i've done a 

xset dpms force on

and it still blanks out after 3 minutes

as well as a 

xset dpms 0 0 1800 (the first two values for standby and resume)

when it enters power saving mode, i cannot press any key to regain access to my computer.  

xset -dpms

has no effect as well   xset dpms force on 

is what i believe should have kept it no matter what so i'm at a loss as to what to try.

---

