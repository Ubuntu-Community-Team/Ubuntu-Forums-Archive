---
title: "Broken displays in the calendar in Kontact?"
date: 2009-04-28
forum: General Help
---

### Post by Rulls on 2009-04-28
Just upgraded to 9.04, running KDE 4.2, and it appears that certain views in the Kontact Calendar module are broken.

When you have selected the month view, you see the grid of days of the month with existing appointments displayed.  But when you select day, 3-day, week, or workweek view, the area in which the day or days would be shown is blank.  Even when I select a day range in which there is an existing appointment, the display is blank.

Is anyone else experiencing this problem?  Is this a known bug?  Is there a known fix or workaround?

Thanks in advance for any assistance.

---

### Post by spb37 on 2009-06-11
What worked for me was to manually delete configuration files.  Purge / complete reinstall did not fix the problem.  I went to 
.kde/share/config and deleted all the files relevant to kontact including korganizer files.
Hope this helps someone.  


> **Rulls said:**
> Just upgraded to 9.04, running KDE 4.2, and it appears that certain views in the Kontact Calendar module are broken.

When you have selected the month view, you see the grid of days of the month with existing appointments displayed.  But when you select day, 3-day, week, or workweek view, the area in which the day or days would be shown is blank.  Even when I select a day range in which there is an existing appointment, the display is blank.

Is anyone else experiencing this problem?  Is this a known bug?  Is there a known fix or workaround?

Thanks in advance for any assistance.

---

