---
title: "Video anomolies after kernel upgrade from 389 to 686"
date: 2005-07-03
forum: Desktop Environments
---

### Post by cheeseballs on 2005-07-03
Been hoping around different distros with a Compal CL56 notebook and have only seen this problem in ubuntu. After upgrading to 2.6.10-5-686 via the command apt-get install linux-686 i begin to get strange video anomalies when x starts. Pink, green, blue, etc seem to be along the edges of all fonts and in between edges of objects on the screen.

I thought the problem may have been the driver so I checked xorg.conf to see that it was using the radeon driver. I then began to upgrade ati proprietary drivers. the drivers installed correctly but the problem persisted. 

The fix for the problem is very strange. (at least to me). Running fgl_glxgears, which fails, automatically cleans up all the pixel anomalies.

Any Ideas on why this is happening? Thanks

---

### Post by mohaham on 2005-07-03
this thread might be of some help
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

if the problem persists you would be better off using the 386 kernel..

---

### Post by cheeseballs on 2005-07-03
Thanks. I accessed the thread you recomended today to fix the drivers. I have opengl support now. As soon as I run glxgears all pixels are fixed and everything works fine. I tried going back to the 386 kernel and had the exact same problem with the pixels as with 686. I noticed this problem when I was running ubuntu w/ gnome a few months ago also.

---

### Post by cheeseballs on 2005-07-04
Changing the order of the modules in my  xorg.conf file following the xorg.conf example from the ati Drivers v0.2 thread seems to have fixed the problem.

---

