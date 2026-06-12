---
title: "Windows stuck at top of screen"
date: 2008-09-28
forum: Desktop Environments
---

### Post by outofnapkins on 2008-09-28
somehow I've caused all of my programs to open in windows that are stuck at the top of the screen. I can't move them or resize them. I am running hardy heron gnome ubuntu and have installed compiz fusion and the emerald theme manager. I have spent four or five hours in frustration trying to find a checkbox in a menu somewhere that turns this option off. Maybe it's my imagination but I swear I saw it once when I first installed ubuntu.

---

### Post by p_quarles on 2008-09-28
Well, I'm not sure exactly what you mean, and a screenshot might help clarify.

But, there's something that might help: alt + right mouse button allows you to resize a window without using a handle. alt + left mouse button allows you to move it without using the handle.

---

### Post by Tristesobre on 2008-09-28
Hi, 

Maybe your windows are stuck to the top because you activated Compiz, but you disabled the "place windows" plugin in the Compiz settings.

My two cents.

---

### Post by Kevbert on 2008-09-28
It may be worth turning off Snapping Windows under Windows management in Compiz.

---

### Post by outofnapkins on 2008-09-28
I turned on place windows and that helped, I still can't move them around on the screen but at least they're not stuck at the top anymore.  I also checked the snapping windows feature but it was already turned off.  Now I just need to figure out how to make those darn windows movable.

Thanks for your help.

---

### Post by outofnapkins on 2008-09-28
I tried the alt rightclick method and nothing happened :(

Then I opened the avant window navigator and loaded the compiz icon into a panel at the bottom of the screen.  I clicked on the icon and selected (right clicked) the settings manager at the top of the list and magically - everything works now. Man am I happy. If anyone has an idea of what happened I'd sure love to know what the problem might have been.

Thanks to everyone for their help.

---

### Post by uaPtah on 2011-05-03
Recently updated to 11.04 version, have played a bit with Compiz and I've got same issue.

[COLOR=black]_My solution was to  go to Compiz Config Settings Manager, then preferences and, click on "reset to defaults" button._
[/COLOR]
In my case it seems that enabling Desktop Cube causing this issue.  So, I decided to go with Desktop Wall at least to next Ubuntu release. Hopefully this glitch will be fixed by than.

---

### Post by onionz on 2011-09-06
This is pretty silly, but I fixed it by going to the Compiz Settings Manager and selecting Resize Window and Move Window under Window Management.  They were disabled by default once I installed Compiz.

---

### Post by raiserramon on 2013-01-17
What happened to me was that the window decorations disappeared.  Once I enabled window decoration under the effects tab, everything worked again.  Before that, every Firefox window would open at the top of the screen.

---

