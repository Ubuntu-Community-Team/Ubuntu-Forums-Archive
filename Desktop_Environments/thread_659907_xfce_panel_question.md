---
title: "xfce panel question"
date: 2008-01-06
forum: Desktop Environments
---

### Post by fouadk on 2008-01-06
hi everyone...

i was using gnome until i tried kde then i switched to gnome coz i did not like all the extra fancy environment so i decided to give xfce a shot....i liked it a lot since my computer is not so powerful...i like gnome but xfce is lighter but the only thing i don't like till now is the lack of ability to drag and drop items into the panel...in gnome i drag and dropped a terminal icon into the panel for instance....in xfce that does not work???

another thing is in gnome when u press the quit button there is an option to lock the screen...i cant find that in xfce....

please help...

thanks in advance

---

### Post by adam.tropics on 2008-01-06
You could always just use gnome-panel....even in xfce.

---

### Post by urukrama on 2008-01-06
> **fouadk said:**
> i was using gnome until i tried kde then i switched to gnome coz i did not like all the extra fancy environment so i decided to give xfce a shot....i liked it a lot since my computer is not so powerful...i like gnome but xfce is lighter but the only thing i don't like till now is the lack of ability to drag and drop items into the panel...in gnome i drag and dropped a terminal icon into the panel for instance....in xfce that does not work???

No, this doesn't work in Xfce.

> **fouadk said:**
> another thing is in gnome when u press the quit button there is an option to lock the screen...i cant find that in xfce....

You could create a custom menu entry (with the menu editor under Settings > Menu Editor), or add a panel launcher for it. Use either of the following commands, depending on which screensaver you have installed or prefer:

For xscreensaver use: xscreensaver-command -lock

For gnome-screensaver use: gnome-screensaver -command --lock

---

### Post by fouadk on 2008-01-07
thanks everyone for your quick help....

how do u add a gnome-panel in xfce ????

---

### Post by adam.tropics on 2008-01-07
As far as I remember,(been a while) install gnome-panel (it will install gnome-panel-data and may be a little more, not sure) then run it! <alt>F2 for run work in xfce?  If all works add it to your start up. Last time I tried the only problem I had was forgetting to remove xfce panel first,, so on login they both started.

---

### Post by urukrama on 2008-01-07
Btw, you can also [use gnome-panel-applets on xfce4-panel]("http://bapoumba.wordpress.com/2008/01/04/add-gnome-applets-to-the-xfce-panel/").

---

### Post by adam.tropics on 2008-01-07
> **urukrama said:**
> Btw, you can also [use gnome-panel-applets on xfce4-panel]("http://bapoumba.wordpress.com/2008/01/04/add-gnome-applets-to-the-xfce-panel/").

I didn't know that. Cheers

---

