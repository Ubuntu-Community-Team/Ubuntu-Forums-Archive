---
title: "compiz bug."
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by c_plus_plus on 2007-11-06
I had a hard time getting compiz to start, but i eventually got it working: Every time I ran compiz --replace, my x windows crashed. I traced this down to the command "xvinfo" in /usr/bin/compiz. This command was used to check for xgl. knowing I didn't have xgl, I mearly edited the script for the asssumption the user doesn't have xgl. This worked fine until I got a compiz upgrade. It took me a while to figure that the reason Gnome wouldn't start was because the upgrade put the file back the way it was. Is there any way to fix this bug? I didn't know where to put this, in ubuntu bugs, compiz bugs, or x windows bugs. A short-term fix would be to keep ubuntu from replacing my edited /usr/bin/compiz file with a new one.

---

### Post by Forlong on 2007-11-07
So if you run ```
xvinfo
``` now in a terminal kills X for you?

That's certainly not a bug in Compiz but I have no idea what could possibly cause this.
You should definitely trace the issue - consider starting an own thread for that, where you specifically address this.

---

