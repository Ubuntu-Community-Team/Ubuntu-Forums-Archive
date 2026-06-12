---
title: "gnome-system-monitor:  Change time span graphed?"
date: 2015-03-19
forum: Desktop Environments
---

### Post by 1clue on 2015-03-19
Hi,

The gnome-system-monitor graphs a 60-second window of resource usage.  I'd like to change that to 3 minutes.

Is there some hidden setting for that or do I need to alter source?

Thanks.

---

### Post by tgalati4 on 2015-03-19
You would think that there is a gconf setting that you can change.  You would think that you could change a Preferences setting to change the time scale.  You would think that you can simply click the "60" and change it to "300".

No.  You can do none of those things.

Perhaps look through the source code and find the time value and change it and recompile.  Because it is a CPU hog, there are better monitoring tools like *htop*.  Perhaps that is why the time scale can't be changed--it was not intended for long-term usage.

---

### Post by 1clue on 2015-03-19
CPU hog:  Pretty much anything gnome, IMO.

Generally speaking I agree with you about htop, but for the current task I need the pretty graphics.  I need to take screen shots of activity over time.

I suppose I'll look for other things, but this was the easy route.

---

