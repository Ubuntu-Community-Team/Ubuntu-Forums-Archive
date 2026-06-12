---
title: "Removing Suspend and Hibernate options from log out?"
date: 2007-12-16
forum: Desktop Environments
---

### Post by crispycritter911 on 2007-12-16
What do I need to remove suspend and hibernation from Gnome's log out options. I have tried to get suspend and hibernation to work but is proving to be rather problematic. Thank you
Crispy

---

### Post by scottmuz on 2007-12-16
Enter
gconf-editor /apps/gnome-power-manager/general 
from the command line and then deselect 
can_suspend and can_hibernate

---

### Post by crispycritter911 on 2007-12-16
Thank you very much.
-Crispy

---

