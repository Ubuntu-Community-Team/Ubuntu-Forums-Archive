---
title: "Help!  Installed compiz settings manager, now Unity is gone!"
date: 2011-10-29
forum: Desktop Environments
---

### Post by lbeidler on 2011-10-29
Ubuntu 11.10 on an hp laptop
Everything was working GREAT until I installed Compiz settigns Manager.  
Now Unity is gone! the launcher bar is gone, the bar on top of the screen is gone, everything.  i tried typing 'unity" from a terminal, and it didn't start.  I tried uninstalling the settings manager, that didn't work.  Please help!
Thanks.

---

### Post by lbeidler on 2011-10-29
Solved!  I inadvertently turned off the unity plugin in the settings manager.

---

### Post by Nolt on 2011-10-31
Thanks for explanation, I was wondering what happens. I installed compiz settings manager and only changed water windows effect and then Unity crashes. I had only one bar at the top. Alt+F2 doesnt worked only combination to log out alt+ctrl+del. When I ran in Ubuntu 2D mode all was OK.

I will check this. Thanks again.

---

### Post by Mark Phelps on 2011-10-31
I've had the same problems.  Evidently, all you have to do is install ccsm and OPEN it!  You don't have to change any parms, just run the app, and UNITY is trashed.

Yet another FINE example of Canonical pushing some garbage out the door with, obviously, not enough testing.

The fix is to remove unity and compiz, reinstall compiz and unity, and NOT reinstall ccsm -- see link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by JasonR on 2011-10-31
> **Mark Phelps said:**
> I've had the same problems.  Evidently, all you have to do is install ccsm and OPEN it!  You don't have to change any parms, just run the app, and UNITY is trashed.

Yet another FINE example of Canonical pushing some garbage out the door with, obviously, not enough testing.

The fix is to remove unity and compiz, reinstall compiz and unity, and NOT reinstall ccsm -- see link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

This happened to me.  I did nothing but open ccsm and Unity 3d vanished.  Apparently just opening the app is enough to uncheck the Unity plugin, which causes the problem.  Now I'm back with 10.04.

---

### Post by Justinba1010 on 2011-10-31
CCSM works fine for me. I might already be in 2d mode :D.

---

### Post by roger_1960 on 2011-10-31
Hi

If you have a problem, try
> 
CTR ALT T

and then
> 
unity --reset

I installed and opened ccsm in Unity 3D with no problems at all.  However, quite a few settings in ccsm are not compatible with the unity plugin.

---

### Post by Mark Phelps on 2011-11-01
I tried unity --reset and it trashed the display majorly.  Only fix was to do all the commands in the link I provided.

---

