---
title: "Move panel from top to side"
date: 2009-11-24
forum: Desktop Environments
---

### Post by axel112 on 2009-11-24
Hi there!

Is it possible to move the top panel to either left or right side?

I have looked in .gconf but I can't see any configfiles that makes me able to achive this.

peace /axel

---

### Post by drs305 on 2009-11-24
It's too easy. Click and drag, or right click the panel, Properties, Orientation.

Good for you for looking in gconf! They are found here:
/apps/panel/toplevels/bottom_panel_screen0/orientation
/apps/panel/toplevels/top_panel_screen0/orientation


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by axel112 on 2009-11-28
Hi there!

I'm running netbook remix. Rightclick or click and move isn't possible. Or?

I wonder if there is some config files in /usr/netbook?

---

### Post by etnlIcarus on 2009-11-28
It shouldn't be locked-down, to my knowledge. Make sure when right-clicking the panel that you're clicking in an *empty* space. If you right-click over the tasklist or any other 'applet' *in* the panel, you'll only get options for that applet.

---

