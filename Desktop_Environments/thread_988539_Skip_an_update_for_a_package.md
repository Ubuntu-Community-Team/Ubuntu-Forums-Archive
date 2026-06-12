---
title: "Skip an update for a package?"
date: 2008-11-20
forum: Desktop Environments
---

### Post by kLAcK on 2008-11-20
Is there a way to tell Synaptic Package Manager to skip an update?  Seamless in rdesktop is borked in 8.10 so I had to install the generic debian version.  My problem is that Update Manager keeps telling me to install the ubuntu version because it thinks its newer.

---

### Post by Shazaam on 2008-11-20
Open Synaptic, find your offending package, highlight it. Then go to Package>Lock version and check the box. If you want to update the package later you will need to undo this. Remember, this stops ALL notices of updates for that particular package including Security updates.

---

### Post by kLAcK on 2008-11-20
Thanks works perfect!

---

