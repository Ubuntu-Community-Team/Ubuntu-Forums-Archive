---
title: "Cannot enable more than 2 workspaces"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by potatan on 2007-12-11
Hi,

I'm using Gutsy 7.10 with an ATI Radeon X800 Pro (working just fine after a few headaches).

I've managed to install Compiz and have lots of nice effects, but cannot get a cube.  I believe this is because I only have two workspaces, yet when I right-click the workspace and choose different rows/columns, it stays at 1row x 2column.  

I have tried restarting X and also rebooting, but whatever I set the number of workspaces to, I only ever see two of them.  See screenshot showing selection of 2x2 workspaces, but with only 1x2 in the system area.

Any ideas?  I think this worked before I installed Compiz, but of course I didn't get all the effects then.

Many thanks

---

### Post by jryprt on 2007-12-11
Try making it Columns 4  & Rows 1
that should give you a cube 4 workspaces

---

### Post by mcduck on 2007-12-11
You'll need to configure that in Compiz settings.

Install 'compizconfig-settings-manager' if you haven't got it already, then go to System/Preferences/Advanced Desktop Effects Settings. From there you can select what plugins you want to use and how they should behave.

To get the cube effect you'll need to have Desktop Cube and Rotate Cube plugins enabled, and the amount of workspaces is controlled in General Options, just set the Horizontal Virtual Size to 4 in the  Desktop Size-tab.

---

### Post by potatan on 2007-12-11
Thanks, all works now.  I had exhausted playing with all the various cube options, turning them off, on, etc.  Completely failed to spot that there was a General options setting too!

Still have nothing on the top/bottom of the cube, but I'll carry on having a dig around.

Cheers.

---

### Post by mcduck on 2007-12-11
> **potatan said:**
> Thanks, all works now.  I had exhausted playing with all the various cube options, turning them off, on, etc.  Completely failed to spot that there was a General options setting too!

Still have nothing on the top/bottom of the cube, but I'll carry on having a dig around.

Cheers.
Top and bottom images are handled by the Cube Caps-plugin (under Utility-category).

Your best bet is to se PNG images, with sizes as powers of 2 (for example 1024x1024 works, 512x512 works and 2048x512 works but 1000x1000 doesn't work).

Set the images under the Appearance-tab and then make sure that drawing of the images is enabled in the Behaviour-tab.

---

