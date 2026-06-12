---
title: "Need a hint on adjusting screen gamma permanently"
date: 2012-09-20
forum: Desktop Environments
---

### Post by s.v.z on 2012-09-20
Good time of day, everyone! I'm facing this problem with my Ubuntu 12.04.1 and a new ViewSonic monitor. The trouble is that the monitor has it's default gamma value set too high and there is no way I can adjust it by monitor controls. 
So far I've been using the ```
xgamma -gamma .7
``` command to get a comfortable picture. The problem is that after the system is locked or after I go to the "Switch User" menu gamma is reset back to 1.0 level. What can I do to adjust it once and for all times?

---

### Post by AMSlider on 2012-09-20
I don't have a solution to your issue.  But I tried your command and my screen looks better!  Some ideas to checkout could be a gamma setting in xorg.conf.  Or RedShift, as it sort of does the same thing.  You might be able to investigate their code as it always changes the screen back after a lock or user change.

---

### Post by jdrichardson on 2012-09-21
You need to add this command to your startup applications:

/usr/bin/xgamma -gamma 0.7

You add startup applications by selecting "Startup Applications" from the drop-down menu shown when you hit the exit button in the upper right-hand corner of the screen. Under startup applications preferences, select "Add", then fill-out the add-startup-program form. Add the above command in the "command" entry.

Hope this helps.

---

### Post by AMSlider on 2012-09-22
> **jdrichardson said:**
> You need to add this command to your startup applications:

/usr/bin/xgamma -gamma 0.7

You add startup applications by selecting "Startup Applications" from the drop-down menu shown when you hit the exit button in the upper right-hand corner of the screen. Under startup applications preferences, select "Add", then fill-out the add-startup-program form. Add the above command in the "command" entry.

Hope this helps.

I think the OP had it in the startup apps, but was having issues with it when he switched users or unlocked the screen.  I just looked at the command line options for redshift and it has the gamma functionality (plus lots of others).  So, he needs to add the following to the startup applications after he's installed redshift (It's in the ubuntu repository):

```

/usr/bin/redshift -t 6500K:5000K -g .7:.7:.7

```

Cheers

---

