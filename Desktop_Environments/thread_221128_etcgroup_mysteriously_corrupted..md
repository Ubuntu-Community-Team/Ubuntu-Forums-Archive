---
title: "/etc/group mysteriously corrupted."
date: 2006-07-22
forum: Desktop Environments
---

### Post by enthusiast on 2006-07-22
Hi,
I found out I could not use the admnistrative menu items on all admin account. It was strange.
Then I looked at the /etc/group file to determine if it were permissions.

All users in the the "admin" group were missing. I had to su - and luckily I had enabled root. I added my main account and was okay again.

Anyone found a source causing problems, etc the User/Group manager?

---

### Post by aysiu on 2006-07-22
That is lucky, but there's also something called "recovery mode," which will make you root, too.

---

