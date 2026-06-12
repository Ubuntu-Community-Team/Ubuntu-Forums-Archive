---
title: "Disabling &quot;Switch User&quot; option in Screensaver"
date: 2006-03-09
forum: Desktop Environments
---

### Post by doteus on 2006-03-09
Hello. I want to know if there is a way to disable the "Switch User" option when I "block" the screen, since this allows someone else (namely... my daughter!) to reboot or shutdown the computer.  If you think about it, this doesn't actually protect you computer from unauthorized use. 

Thanks a lot

---

### Post by FIONEX on 2006-03-09
Well even if you take it out, what's stopping your daughter from pressing the reset button, unless you pried it off.  And in such a case, she'd unplug the computer.  And even if you bolted the plug into the wall, what's stopping her from flicking off the circuit breaker to the house? ;)  Like your session won't be erased if she decides to use the switch user button.

---

### Post by MaX on 2006-03-09
I understand what he's aiming at.
If I let my brother/mother etc log in to the computer they'll forget that I was logged in first and they'll shut it down.

If they have to call for me to log out first I'll be safe.

---

### Post by KirkoR on 2006-09-18
You can go to gconf-editor and find this path:
/apps/gnome-screensaver/user_switch_enable >> UNCHECK
Done :)

---

