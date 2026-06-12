---
title: "Blank desktop after start"
date: 2009-06-19
forum: Desktop Environments
---

### Post by kxunil on 2009-06-19
Blank Desktop! Ubuntu 8.10 startup splash screen displays fine then desktop is blank with mouse pointer in the center of the light brown screen? Perplexed, have looked for solutions and have conceded. 

This is not a new install. However, awhile ago I did go through and remove packages that I thought I did not need. Any help appreciated. Thanks in advance.

Problem solved. I entered command prompt Ctrl+Alt+F1, at the prompt entered nautilus, which did not exist. Used apt-get install install nautilus. Rebooted the machine and other than a minor panel error all is back to normal. We live and learn :o)

---

### Post by Sarai the Geek on 2009-06-19
> **kxunil said:**
> Blank Desktop! Ubuntu 8.10 startup splash screen displays fine then desktop is blank with mouse pointer in the center of the light brown screen? Perplexed, have looked for solutions and have conceded. 

This is not a new install. However, awhile ago I did go through and remove packages that I thought I did not need. Any help appreciated. Thanks in advance.

Problem solved. I entered command prompt Ctrl+Alt+F1, at the prompt entered nautilus, which did not exist. Used apt-get install install nautilus. Rebooted the machine and other than a minor panel error all is back to normal. We live and learn :o)

Ah yes, deleting nautilus is really never a good idea unless you plan to replace it with a different file browser!

---

