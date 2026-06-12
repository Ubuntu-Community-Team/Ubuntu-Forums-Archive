---
title: "Xorg process scheduling"
date: 2008-12-27
forum: General Help
---

### Post by thefirstM on 2008-12-27
I have a question about process scheduling in Linux.  I was trying to run Xorg with a higher priority (nice) level to make sure the cursor did not jerk when the system was under load.  However, this did not work very well.  I found out that using Ksysguard as root, I can set Xorg to use Round Robin scheduling, which fixes the problem.  Is there some way that I can change Xorg to use Round Robin scheduling using a text command?

---

