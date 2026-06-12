---
title: "Changing main 'admin' user..."
date: 2006-08-12
forum: Desktop Environments
---

### Post by Spudgun on 2006-08-12
During the installation of Ubuntu, as you are all aware, Ubuntu asks you to supply a username and password of the 1st user. Now I'm pretty sure this user is considered the main 'admin' of the system.

What I want to know is, is there a way of changing who's the main 'admin' to be another user?

Many thanks in advance.

---

### Post by aysiu on 2006-08-12
Yes, there's a way, but be very careful about this.

I would do this: ```
sudo cp /etc/group /etc/group.backup
sudo adduser *secondusername* admin
``` Then, log in as *secondusername* and then do ```
sudo deluser *firstusername* admin
```

---

### Post by Spudgun on 2006-08-12
Thanks for the reply, but is there way of doing it if I've created the user already?

---

### Post by aysiu on 2006-08-12
Yes. That *is* the way you do it if you've created the user already. *suo adduser secondusername admin* adds the existing user *secondusername* to the *admin* group.

---

