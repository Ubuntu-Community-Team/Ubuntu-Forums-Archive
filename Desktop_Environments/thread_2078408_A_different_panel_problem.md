---
title: "A different panel problem"
date: 2012-10-30
forum: Desktop Environments
---

### Post by JKyleOKC on 2012-10-30
While chasing other problems on a 12.04 online upgrade from 8.04 through 10.04, I somehow managed to move the top panel down its own width from the top of the screen. It now obscures a strip of any maximized application.

I found an XML file in one of the hidden configuration directories of my home directory that purports to contain the offsets, sizes, and icons/applets/launchers for both panels. However it still shows a y-offset of 0, although the panel actually appears at what seems to be a y-offset of 36 or so. Rebooting makes no difference; it stays at the offset.

Where else might this information be stored, in xfce 4.8 or xfdesktop configuration files?

---

### Post by drezabek94 on 2012-10-30
I haven't used XFCE, so I don't know the exact location of the configuration files. You could try moving the xml files out of the directory, and after restarting it should create a new default one. You could then try to configure the fresh configuration file to match the old one via the GUI, and hopefully that will "fix" it.

You probably don't want to do that if it will take more time to reconfigure than to fix the old one though.

---

### Post by lightning slinger on 2012-10-31
Have you not just tried to move the panel back to it's original position with,
Settings Manger > Panel > Unlock Panel, once panel is unlocked two 'handles' will appear at either end of the panel, grab a 'handle' and move the panel to where you want it to reside then go back to Settings Manager > Panel and Lock Panel again.

---

### Post by JKyleOKC on 2012-10-31
Thanks, Lightning Slinger! That led to the solution, although in Xubuntu there are no handles on the panel and the lock/unlock option is in a different place.

In Xubuntu, the option is in "Panel preferences" which can be reached by right-clicking any option and choosing that entry from the context menu. Lock/unlock is controlled by a checkbox in the resulting dialog.

When the checkbox is cleared, the panel is outlined by a dashed border that's about one pixel wide. That border provides the handle. Once it's checked again, or the mouse is clicked anywhere away from the border, the border goes away.

Apparently I had unlocked the panel, accidentally clicked on that near-invisible border (which isn't documented in any of the panel help screens I found), and begun a move operation. When I clicked on the blank desktop to get rid of the "move" mouse pointer, that put the panel in its new position.

Reversing the steps brought the border back and let me slide the panel back to its normal top-of-screen position. It's now locked and won't be unlocked again unless I decide to move it somewhere else!

Thanks again!

---

