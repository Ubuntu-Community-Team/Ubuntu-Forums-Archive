---
title: "MesaGL problem"
date: 2012-07-05
forum: Desktop Environments
---

### Post by ajfountain on 2012-07-05
I have a problem, and wonder if anyone can help me with it.

CAD/CAM application, save image to file, in a MesaGL environment, the saved image (any format at all, and I can chose from many) seems to have a problem with scaling. The green factor of the image seems to be scaled wrongly, so that whereas on the screen red/green/blue factors all appear ok, in the image, the green parts of the image are left shifted and smaller. So something is being scaled incorrectly, I surmise.

If I run xscope, all that appears to go through the system which is pertinent from point of clicking on the interface buttons are a GlxRender and GlxMakeCurrent call.

From /var/log/Xorg.0.log, direct rendering is off.

Id like to debug this - but have little idea where to go to look, the CAD/CAM application isnt mine, and I dont have sources. I am running under the hypothesis that its the X environment that is broken, because running the same application on a version of RH doesnt have the issue.

Any ideas where to look? Is this a known problem seen in the past?

Many thanks for any directions and assistance!

---

