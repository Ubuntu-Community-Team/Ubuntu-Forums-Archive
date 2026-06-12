---
title: "Weather applet uses old location"
date: 2011-09-07
forum: Desktop Environments
---

### Post by scprotz on 2011-09-07
Hi All,

I recently moved from TX to KY.  I've been trying to update date/time and weather of my ubuntu desktop, but for some reason, even if I change the location, (right click time/weather applet, choose preferences, go to locations tab, remove all locations, add my new location with accurate GPS code), It still shows the weather for TX, not KY.

Any insights on why this happens or how I might fix it?

I've searched the forums but can't really figure this one out.

Thanks

-scprotz

---

### Post by Frogs Hair on 2011-09-07
I don't know if this would help , but part of your new state is in the central time zone and part in the eastern . Have you changed your time zone in Time & Date settings if needed . You could also reset the panel applets with the following command and try to enter the location again . This is for the Gnome panel not Unity.

Code:
 gconftool --recursive-unset /apps/panel && killall gnome-panel

---

### Post by scprotz on 2011-09-08
Thanks for the reply.  Not sure what ended up causing it.  I had already set the timezone to ET instead of CT.  I came back in this morning and 'reset' the location, and it started working (so far).  I'll let it run a bit and then come back and see if it sticks.
-scprotz

---

### Post by Frogs Hair on 2011-09-08
I'm glad it  worked out for the moment any way .

---

