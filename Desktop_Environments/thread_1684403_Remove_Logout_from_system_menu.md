---
title: "Remove Logout from system menu"
date: 2011-02-09
forum: Desktop Environments
---

### Post by edgreenberg on 2011-02-09
On 10.04, Lucid, I have a need to adjust the system menu for one of our accounts to remove the Log Out [Name] item. 

It's a rather embarrassing problem involving the nVidia driver, a laptop, a dock and dual monitors, where ending a gnome session sems to crash the video driver (or even the whole computer, I'm not sure)   :)

Can somebody tell me where I can adjust the contents of the system menu either for the whole system or for particular users? 

Thanks,

Ed Greenberg.

---

### Post by kerry_s on 2011-02-09
open the terminal & run "gconf-editor"

use the edit-> search to find the log-out entries

---

### Post by Krytarik on 2011-02-10
> **kerry_s said:**
> open the terminal & run "gconf-editor"

use the edit-> search to find the log-out entries
To be exact, it is here:
/apps/indicator-session/suppress_logout_menuitem

---

### Post by kerry_s on 2011-02-10
> **Krytarik said:**
> To be exact, it is here:
/apps/indicator-session/suppress_logout_menuitem

there should be 1 for the menu(under "system" on the panel) to.

i'm on my google notebook is why i can't check the paths & post.

---

### Post by Krytarik on 2011-02-11
> **kerry_s said:**
> there should be 1 for the menu(under "system" on the panel) to.

Yeah, you're right, found this one: /apps/panel/global/disable_log_out
But if indicator-session is at the panel, those options in the System menu are disabled anyways.

PS: Great, now I have to re-arrange my panel items, again. ;-)

EDIT: If you disable those, you also can't shutdown. :-D

---

### Post by kerry_s on 2011-02-11
yeah, thats the 1 to use, covers all.

---

### Post by cccc on 2011-04-29
I've removed Logout from system menu using "gconf-editor":

/apps/panel/global/disable_log_out

but the problem is the "Shut Down" Applet will be removed as well.
Howto make "Shut Down" active and remove only Logout?

---

