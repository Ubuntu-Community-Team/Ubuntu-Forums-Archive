---
title: "desktop gone, unable to made sudo changes"
date: 2009-03-15
forum: General Help
---

### Post by dave37 on 2009-03-15
I'm trying to help a friend overseas, his Hardy installation is not displaying the task bar, desktop icons, or allowing him to make any changes requiring sudo, for his user.  Other users have a normal desktop.  I was going to walk him through creating a new user as the simplest way to get him going again, but this of course requires administrator privileges and for some reason his user has lost sudo capability.  How can I grant his user sudo privileges?  No other user on the machine other than his was set up with sudo privileges.

He is using the gnome desktop

Thank you

---

### Post by kanikilu on 2009-03-15
Can your friend boot into recovery mode? This should give him root access to, if necessary, add himself back into the "admin" group, and/or try creating a new user.

From the root shell in recovery mode:

To find out what groups his current user is in, he can do: ```
groups username
``` if "admin" isn't listed, probably the easiest solution would be to do ```
usermod -G username admin
``` Optionally, you can use **useradd** to create a new user and then **usermod** to add the new user to the admin group, and other groups as necessary.

---

### Post by dave37 on 2009-03-15
I will try that, thank you!

---

### Post by dave37 on 2010-01-12
[solved]  Once I was back overseas and in front of my friend's computer I was able to log in using his user, one of his children had deleted the desktop icons and panels.  I simply added the needed panels and icons and all is good.

---

