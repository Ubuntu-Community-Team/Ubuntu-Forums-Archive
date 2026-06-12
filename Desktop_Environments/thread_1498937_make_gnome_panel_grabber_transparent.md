---
title: "make gnome panel grabber transparent"
date: 2010-06-01
forum: Desktop Environments
---

### Post by Ebener on 2010-06-01
My gnome panel currently looks like this:

[IMG]http://img34.imageshack.us/img34/9450/fototg.png[/IMG]

The panel is not expanded and the autohide buttons are not checked. As you can see I've set the background to transparent and removed the shadow via ccsm. The only thing that doesn't look nice are the "grabbers" to move the panel arround. Can they be modified to be transparent too? Maybe editing the theme?

Before someone suggests it: I cannot set the panel to expand because I use a dock which would be partly covered by the panel.

---

### Post by Ebener on 2010-06-05
I've solved it with a trick. 
If anyone is interested, here is how I've done it: Set the panel to expand, but in ccsm set the window rule: below for "name=gnome-panel". This way the panel does not lay itself on top of the dock anymore. Of course you could do the opposite and set your dock in the above rule. Hope that helps someone someday. :)

---

### Post by ThomasB2k on 2010-07-06
Unfortunately that doesn't seem to have worked for me

---

