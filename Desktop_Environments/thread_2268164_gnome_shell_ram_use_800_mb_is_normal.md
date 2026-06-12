---
title: "gnome shell ram use 800 mb is normal ?"
date: 2015-03-06
forum: Desktop Environments
---

### Post by cosy2 on 2015-03-06
Hi forum, like the title say i want to ckeck if the ram usage for gnome shell is normal to start under 200 and run up to 800.


Tia

---

### Post by kerry_s on 2015-03-06
yes, it will make use of ram for speed. your not doing nothing else with that ram are you ?

---

### Post by cosy2 on 2015-03-06
> **kerry_s said:**
> yes, it will make use of ram for speed. your not doing nothing else with that ram are you ?

just wanted to know if is normal :D

---

### Post by kerry_s on 2015-03-06
yeah, newer kernels are making better use of ram if available. i'm using elementary os & i see that same kind of use, boot's about 200+mb & go's up from there as you use apps.
i have 2gb & notice it will use up to just under a gig, but everything does feel faster. :)

---

### Post by buzzingrobot on 2015-03-06
Yes, I'd say 800mb for the gnome-shell process itself is excessive.  In my experience, it's typical for gnome-shell to be at 150-200mb immediately after logging in, and growing somewhat during a session.   Some previous gnome-shell versions appear to have had a memory leak that would eventually gobble memory along the lines you see, but I've never seen that in current versions.

If you use any extensions, disable them as a test.  Perhaps one of them is the culprit.

You can restart gnome-shell by logging out and in, or simply by doing an alt-f2 and entering an 'r' in the dialogue box that's displayed.

---

