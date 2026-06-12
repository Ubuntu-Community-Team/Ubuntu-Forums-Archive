---
title: "'hibernate' button - how to change"
date: 2006-09-09
forum: Desktop Environments
---

### Post by aum on 2006-09-09
Hi,

I just did an install of dapper, and noticed that the 'hibernate' button doesn't work. Sometimes it shuts down the box, but the system just hangs on restart. Sometimes the button has no effect at all.

So I followed the howto for installing suspend2, the hibernate script and the suspend2-enabled kernel.

hibernate/suspend2 works brilliantly, but I'm having to activate it from the command line.

Is there any way to change the action of the 'hibernate' button in the gnome menu, so it executes my hibernate script?

Cheers
aum

---

### Post by mikelygee on 2006-10-15
I think I've finally figured this one out.

Edit /usr/share/hal/scripts/hal-system-power-hibernate, so that it looks for /usr/local/sbin/hibernate first. The default script looks for /usr/sbin/hibernate (which wasn't were I installed it), but after /usr/sbin/pmi. Since it finds /usr/sbin/pmi, it never bothers looking for the suspend2 hibernate script.  

Now when I invoke "hibernate" from the exit menu, I get the suspend2 progress messages, just as if I "sudo hibernate" from the command line.

---

