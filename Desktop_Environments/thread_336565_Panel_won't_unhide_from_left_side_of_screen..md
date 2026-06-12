---
title: "Panel won't unhide from left side of screen."
date: 2007-01-11
forum: Desktop Environments
---

### Post by kuripot on 2007-01-11
Hi All,

I moved my bottom panel to the left side of the screen, and now it will not unhide. I know its still there because I can see the edge of the hidden panel, at least I think that's what it is?? When it was on the bottom I had it set to autohide and used gconf-editor to set "hide_delay" and "unhide_delay" = 500, and "auto_hide_size" = 6  

I tried to force it to show by changing values in the gconf-editor by changing the "auto-hide_size" = 50 and changing "orientation" = bottom to no avail. 

How do I get the panel to show itself again?

In the meantime, I created a new bottom panel, but I noticed in gconf-editor that there is only an option to edit 2 panels, bottom and top. How do I edit this third panel, or say a fourth in the future? 

This is using Dapper with Gnome 2.14.3 with Beryl. 

I've had less than a weeks experience with Ubuntu so if you need any more info please ask.:)

---

### Post by kuripot on 2007-01-12
Any ideas for either question?

---

### Post by kuripot on 2007-01-14
I was able to get the left panel to unhide by changing my session to "System default Session" at the login menu. I deleted my new bottom panel and brought down the panel on the left side. Restarted X and everything works.
 
I'd still like an answer to question 2 if in the future I do decide to have more than 2 panels.

---

### Post by manutdfan2850 on 2007-01-19
i have the same problem. the left and right panels will not come back from autohide if using beryl, but the top and bottom will. 

under gnome all panels will work as normal 

any help? thanks in advance

---

### Post by munkar on 2007-02-25
i have exactly the same problem

> **manutdfan2850 said:**
> i have the same problem. the left and right panels will not come back from autohide if using beryl, but the top and bottom will. 

under gnome all panels will work as normal 

any help? thanks in advance

---

### Post by manutdfan2850 on 2007-02-26
> **munkar said:**
> i have exactly the same problem

if anyone has any solution to this problem, plz help.  thanks

---

### Post by wilberfan on 2007-03-15
Just adding my name to the list...    

Just got beryl 0.2 working on Edgy.  All seems well, except for this panel problem.

---

### Post by bbevol on 2007-03-20
I had to change the auto_hide size in the config for my panel in order to get 2 working.

---

### Post by mcduck on 2007-03-20
This is pretty much a bug related to using Beryl. I'd recommend to not have autohiding panels on left/right side when running Beryl, I don't thing anybody actually knows what causes this problem so it's not likely to get fixed any time soon.. (it could be related to left/right sides not actually being left/right sides of the desktop as the desktop is stretched to all four sides of the cube).

Autohiding on top/bottom works fine in Beryl.

edit: moving mouse up and down at the side of the screen will sooner or later unhide the panel. And you can of course use gconf-edoitor to disable autohiding if you can't get your panel to unhide any other way.

---

