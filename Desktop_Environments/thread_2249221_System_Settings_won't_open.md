---
title: "System Settings won't open"
date: 2014-10-20
forum: Desktop Environments
---

### Post by Phil Binner on 2014-10-20
I have just built a computer from second hand parts and loaded the XUbuntu desktop over Ubuntu 14.4.  The first thought is that I love it.  I've never been comfortable navigating around Unity, and this is clean and quick the way Ubuntu used to be.  There are a few problems, however, also the way Ubuntu used to be.  When I click the settings icon in the top bar it looks the same as in regular Ubuntu, but when I select "System Settings" or "About this Computer" nothing happens.

Another problem is that although the status bar at the top offers the option to "move", it refuses to do it.  I can't see any option other than drag and drop, and if I do this it just pop's back. Where it is it keeps interfering with browser tabs.

The spec is:

Motherboard - Asus P8 Z77-VLX
Processor - Intel I5 2500 3.3Ghz
Ram - 16 GB

Any help please.

---

### Post by buzzingrobot on 2014-10-21
Manuever through the menu -- icon on panel's far left -- for "Settings Manager".  What happens? XFCE's settings tools can be accessed individually via the menu, but they are all grouped under "Settings Manager". 

It's unclear, but if you are seeing a Unity panel when you click something on the right side of the XFCE panel, something may have gone wrong in the install.

---

### Post by Dennis N on 2014-10-21
Xubuntu Desktop 14.04 package (xubuntu-desktop) includes the "Whisker Menu" (xfce4-whiskermenu-plugin) seen in the attachment. So named because the menu's icon shows a mouse (with whiskers). The panel could be on the top (default) or bottom (pictured). You can also create additional panels. "Settings" is the right-most icon on the top bar of the menu window. Hope that helps.

---

### Post by Phil Binner on 2014-10-21
I see how to add another panelat the bottom, and therefore how to move all the items and delete panel 0, is there an easier way, just to move panel 0 to the bottom rather than the top or right.  if so, can you tell me how please.

---

### Post by Dennis N on 2014-10-21
> **Phil Binner said:**
> I see how to add another panelat the bottom, and therefore how to move all the items and delete panel 0, is there an easier way, just to move panel 0 to the bottom rather than the top or right.  if so, can you tell me how please.

By default, there is one panel on the top. You can move the entire top panel to the bottom with all the items intact. 

Right click on the top panel and:

select panel > panel preferences
on 'display' tab, uncheck "lock panel"
two 'handles' appear at each end. 
Grab one with the mouse (hold left button down), and pull the panel down to the bottom.
recheck "lock panel"
close the panel dialog

---

