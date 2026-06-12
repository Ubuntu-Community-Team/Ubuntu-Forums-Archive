---
title: "My bar at the bottom is broken!!"
date: 2005-11-23
forum: Desktop Environments
---

### Post by installwizard on 2005-11-23
After using ubuntu for a couple of minutes I ended up play with the Dictionary, searching for words like Microsoft, internet explorer (very funny meanings) then all of a sudden the dictionary just hang..... and did not want to respond... actually nothing wanted to respond.. so I managed to get System Monitor open and I was trying to kill a couple of precesses like dictionary and probably ended a couple of others to.

So I ended up with a working ubuntu except now i just have a blank bar at theb ottom of the screen. When I open a nother window it does not show in the bar, or the desktop switching thingy is also gone... :confused: help

---

### Post by earobinson on 2005-11-23
right click on the bar go to add or something (not at my ubuntu box) then you should be able to add the task bar back in (you deleated the task applet off your panal)

---

### Post by garciadc on 2005-11-23
Happened to me, but I lost the top panel as well (both panels there, just blank)  I went into terminal and typed

killall gnome-panel 

(i think you need sudo too, but don't remember)

if it doesn't work then just type 

gnome-panel

if that doesn't work then I would reboot and try it all over again if gnome-panel doesn't load up correctly on startup.

---

