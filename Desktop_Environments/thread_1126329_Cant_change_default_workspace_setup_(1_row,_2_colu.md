---
title: "Cant change default workspace setup (1 row, 2 columns) setup on second monitor."
date: 2009-04-15
forum: Desktop Environments
---

### Post by Ein2015 on 2009-04-15
So I'm running a dual-monitor setup using two x screens.  I'm happy with everything but this...

My primary monitor has 3 rows and 3 columns of workspaces.  My secondary monitor has the default 1 row and 2 columns of workspaces.  If I try to make any adjustments on the second monitor, it only changes the first.

Is there any way to add workspaces for the second monitor?

Possibly related system details...
8.04 Ubuntu 32bit
Using latest NVIDIA driver (downloaded and installed yesterday)

Thank you everybody for your hard work and dedication. You're why I love Ubuntu!:KSd

---

### Post by caradeporra on 2009-08-31
well, sorry for the slightly delayed response.  I just had this problem with 9.04 and finally figured out a way to change it (hope four months wasn't too long!!). -Please note this worked for 9.04, not sure about any others!

Firstly, you need to install compiz-config if you have not already.  there are several how-to's on this, one being here: [http://ubuntuforums.org/showthread.php?t=1134653](http://ubuntuforums.org/showthread.php?t=1134653)

After this, click on the second screen (anywhere is fine) then type "alt" and "f2" at the same time to open a run dialogue (this is the only way to open the compiz config on the second monitor).  Type ccsm and hit enter.

Next go into the manager and click on "General Options" - it should be at the very top in the middle.  Go to the "Desktop Size" tab and edit it to your liking in there.  Go ahead and edit the other things you want while you are in there.

Note, some things changed will effect the original screen but I am not sure which ones will, and which will not - so just be careful and only change the things you want.

Hope this helps.

---

