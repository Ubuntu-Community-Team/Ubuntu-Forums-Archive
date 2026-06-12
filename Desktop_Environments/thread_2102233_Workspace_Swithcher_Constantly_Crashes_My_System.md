---
title: "Workspace Swithcher Constantly Crashes My System"
date: 2013-01-06
forum: Desktop Environments
---

### Post by Mike10562013 on 2013-01-06
I recently installed Ubuntu 12:10 with Gnome Fallback and added compiz fusion and cairo dock.  I have the cube enabled and it works perfectly.  However, if I ever were to try to just use the workspace switcher in my top panel, it does not work at all.  In fact, it completely eliminates the top panel and the cairo dock so that the only thing I can do at that point is shut the computer down (not by choosing "Shut Down" as their is no option to do that and restart it.  Has anyone else had this issue and if so, what have you done to fix it?  There are a few other things (mainly theme things) that I don't like about Ubuntu 12.10 but this is the only one that is actually a deal breaker which will prevent me from keeping this installation over my 10.10.  Please help!

---

### Post by stinkeye on 2013-01-06
Works fine here in 12.10.
I didn't add compiz fusion and cairo dock though.
Just installed gnome-panel and logged in to the Gnome Classic session.

Check your workspace switcher is set to 1 workspace.
In compiz you only really have 1 desktop and the switcher will adjust the number of
panels according to the number of virtual desktops you have set in compiz.

---

### Post by Mike10562013 on 2013-01-07
Stinkeye, you are a GENIUS!!  I got your reply a few hours ago but was in the middle of listening to a talk show on the internet radio so I didn't want to test it but made the changes you referred to so I could test it when it was done (mainly changing the number of desktops to 1 and the number of Horizontal Virtual Size to 4 instead of both being four and the Vertical Virtual Size being 1 (which it still is).  So, anyone that runs across this same error...
Horizontal Virtual Size should be 4
Vertical Virtual Size should be 1
Number of Desktops should be 1

---

