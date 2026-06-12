---
title: "(another) Beryl and Window Borders"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by kpel on 2007-04-20
Feisty 7.04, Beryl 0.2.1, NVIDIA driver 1.0-9755

What I've tried that hasn't worked:


-Adding

Option "AddARGBGLXVisuals" "True"

to both the Screen and Device section of the xorg.conf file, both separately and at the same time.


-Adding

Option "XaaNoOffscreenPixmaps" "on"

to the Screen section in the xorg.conf file


Double checking my color depth, both through nvidia-settings and manual edit of the xorg.conf file.



Using the *Option "AddARGBGLXVisuals" "True"* line works for the Compiz effects that are built into Feisty along with installing the gnome-compiz-manager to get the cube to work right.  It looks like there's some sort of conflict with the compiz effects that are built into Feisty and the Beryl install, but I'm new so I have no idea how possible that actually is.


Anyone other tricks out there that might work?  Beryl works great except for those missing borders.

Edit: **Fixed!**

Here's how I did it.  Don't know why it worked, don't care. :)

Installed gnome-compiz-manger from the Synaptic Package Manager.
System>Preferences>GL Desktop.  Enable GL Desktop (this should effectively shut down Beryl and run Compiz).
Ctrl+Alt+Backspace
Everything worked.  Confirmed by changing the settings in Beryl.  Side note, using GL Desktop will kill Beryl.

Second update:
If you do even open GL Desktop you'll have to repeat the procedure in order to get it fixed again.  I'm sure there's a small setting that is being switched, but I've only been using Linux for a week.  I'll let some guru figure this one out.

---

