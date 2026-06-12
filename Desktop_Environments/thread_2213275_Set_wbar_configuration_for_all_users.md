---
title: "Set wbar configuration for all users"
date: 2014-03-25
forum: Desktop Environments
---

### Post by Charlotte18 on 2014-03-25
Here's the situation:

I have wbar set as a startup application for all users. Most user accounts are domain accounts. When a user logs on, a home folder is created at /home/likewise-open/DOMAIN/.

The wbar configuration file, to my knowledge cannot be put into /usr/share/ for all users because the file (.wbar) is created in the home folder, not in /home/.config

Does anyone know of a way to share the preferences so that every user sees the same wbar on login?

Alternatively, does anyone know of a script that would copy the .wbar file into the domain users' home folders upon login but before the launching of wbar?

The basic question here is: How do I set the wbar configuration for all users, even users who have not previously logged on and who therefore do not yet have a home folder?

---

### Post by Charlotte18 on 2014-03-26
Well, I found the config file in the folder called /etc/wbar.d

The new users' .wbar file is created based on the way wbar.cfg in set up in /etc/wbar.d

---

### Post by bapoumba on 2014-03-26
Is your thread solved then ?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks!

---

