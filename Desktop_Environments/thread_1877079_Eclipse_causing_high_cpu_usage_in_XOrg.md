---
title: "Eclipse causing high cpu usage in XOrg"
date: 2011-11-07
forum: Desktop Environments
---

### Post by flopin on 2011-11-07
After upgrading to 10.10, Eclipse performance has dropped rapidly, beyond usable. It takes several seconds for gui items to redraw, actions like switching between tabs, scrolling, opening and closing various treed is terribly slow. Top shows xorg process reaching 100% CPU in the meantime. I have tried several things i googled out, no luck

Adding 
    Option         "AccelMethod" "XAA" 
    Option         "RenderAccel" "true" 

to xorg.conf, no result

Changing java backend to java-6-sun, no result

Turning off desktop effects, no result

Switch driver from nvidia to nv, no result

Using Dell Latitude D630c, dual core, GeForce 135M, dual screen.

Switching to single screen helps a bit, so does shrinking the Eclipse window, but still unusable.

Any help?

---

### Post by mattelacchiato on 2012-08-22
I'm have the same problem. I'm using Kubuntu 12.04 64bit with Nvidia 304.37.

Do you have solved this Problem?

---

