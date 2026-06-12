---
title: "Bizarre refresh rate problem"
date: 2006-01-04
forum: Desktop Environments
---

### Post by patsissons on 2006-01-04
I'm not entirely sure if this is KDE specific, but I do know that the problem does not exist in windows (i have not tried gnome or xfce as im pretty sure the problem can be fixed quite trivially).

Here is the problem.  Upon starting the X server, my default resolution is 1600x1200.  This resolution is only possible at 60Hz with my monitor.  For some reason, however, the X server displays 1600x1200 at 75Hz which results in a distorted screen (actually it stretches out horizontally and there are a few horizontal wavy lines).  Fortunately, the KDM is still accessible and i can then log in and set the refresh rate manually back to 60Hz.  I'd prefer not to do this mindless repetitive task every time i turn my computer on.  

Anyone have any ideas on this one?

---

### Post by Perfect Storm on 2006-01-04
Find your monitor manual or google for it. 

Then:

```
sudo kwrite /etc/X11/xorg.conf

```

Under **Section "Monitor"** you'll see **HorizSync** and **VertRefresh**. Now change them with the numbers you have from the manual.


Reboot

---

### Post by patsissons on 2006-01-04
I don't have the manual for my monitor but I had previously researched the proper values for HS and VR.  I have an NEC MS FE950+  and acording to the specs (which can be viewed here [http://www.necdisplay.com/products/ProductDetail.cfm?Product=92](http://www.necdisplay.com/products/ProductDetail.cfm?Product=92) ), these values should be 30-96 and 50-160 respectively.  With these settings, however, the problem persists.  A quick work around I have found to temporarily fix the issue is to force the VR to 60 by setting it to 60 instead of the 50-160 range.  This works for the time being since I rarely ever change resolutions.  But I would prefer to find a more acceptable solution that this.  I am currently looking into the modeline configurations of Xorg but they are rather complicated and I would like to assume that it is not necessary.  The monitor used to work fine a couple of weeks ago.  Something was updated in one of my monthly package updates and has since caused this problem to occur.  I'm not sure what it is because the only packages that were updated according to the synaptic history were the linux headers.

---

### Post by patsissons on 2006-01-04
upon further inspection of the xorg log file and the specs of the monitor, it turns out that my monitor should support 1600x1200 @ 55-76 Hz.  So the monitor is returning the correct information to the server upon being probed.  However, the monitor is still not displaying this resolution properly at any VR other than 60Hz.  With this information I can only conclude that the monitor has somehow become faulty and this issue is no longer a KDE (or xorg for that matter) specific problem.  I'm not sure how windows manages to determin that 60Hz works properly, but i will inspect further into this matter tomorrow.

---

### Post by jonathanm on 2006-01-04
ive had this problem and it seems to be a kde only problem.  i have an AOC monitor and gave up on fixing it and installed ubuntu with gnome which worked perfectly

---

