---
title: "Update manager doesn't show updates for non-admin users"
date: 2008-12-24
forum: General Help
---

### Post by niallporter on 2008-12-24
Hi all,

I put Ubuntu on my parents' PC a while ago (fed up having to reinstall XP everytime I came to visit) and while it works very well for them, I notice that whenever I come to visit and log on with my own login, there are loads of updates to install.

If I log on as one of their accounts there is no "updates available" notification shown.  They both say they've never seen any messages telling them there are updates.  The only difference between their accounts and my own are that mine is a member of the admin group (and therefore has sudo/gksu access) whereas theirs are both normal users.

Is it possible to allow non-admin users to see when there are updates available and apply them without having to grant them membership of the admin group?

Thanks in advance,
Niall

---

### Post by spiderbatdad on 2008-12-24
System>>Adminstration>>Software Sources>>Updates
Offers the option to install some updates "without confirmation."

---

### Post by mikewhatever on 2008-12-24
I think it makes perfect sense not to show updates, since non-admins can't install them anyway. A user must be an admin to install updates.

---

