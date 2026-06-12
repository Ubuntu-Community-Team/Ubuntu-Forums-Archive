---
title: "min/max/close bar is missing?"
date: 2009-01-28
forum: General Help
---

### Post by Robocoastie on 2009-01-28
How do I get the Min/Max/Close "x" buttons back. Every program I open keeps going full screen so I lose the Ubuntu menu bars on the bottom, top, and don't have the min/max/close x anymore.

thanks,

Rob

---

### Post by Wartender on 2009-01-28
try typing metacity --replace in a terminal

---

### Post by Gizenshya on 2009-01-28
this happens to me sometimes.

if I type in a terminal...

metacity --replace

it replaces the theme (including the buttons).  I then have to go back and enable advanced effects, and reconfigure compiz (as it defaults the settings :( )... but it works.  there may be a better way.

---

### Post by dullard on 2009-01-28
If you're using Compiz and Emerald, I find it can be cured by double clicking the title bar (Shade Window).

Doesn't happen very often since I added both of the above to the startup program list in Preferences > Sessions but I still have to do the Shade Window thing occasionally when Ubuntu gets a bit quirky.

---

### Post by Therion on 2009-01-28
Try this...

Open CCSM.
Go to the Utilities section and open the "Workarounds" plugin.
**Un**-check the box for **Legacy Fullscreen Support**.

You may need to log out, and back in, for this fix to "stick".  I can never remember if you do or not.

---

### Post by Robocoastie on 2009-01-28
That worked Therion, thanks.

---

