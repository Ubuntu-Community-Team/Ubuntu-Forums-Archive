---
title: "Firefox loses preferences"
date: 2007-10-27
forum: Desktop Environments
---

### Post by dieresys on 2007-10-27
Hello everyone,
If I run firefox with sudo, I lose all my preferences. Is this a bug or an expected behavior?

System:
Ubuntu 7.10
Firefox 2.0.0.8

Steps:
-BACKUP YOUR PROFILE!!!
-Open a Terminal and type "sudo firefox"
-Close firefox
-Open firefox without sudo, your preferences just flu away

If this is a bug, I will submit it.
Thanks in advance.

---

### Post by taurus on 2007-10-27
First, why do you run firefix with sudo privilege?

Second, if you run **sudo firefox**, it will look at the Preferences of root's, not your account.

---

### Post by dieresys on 2007-10-27
> **taurus said:**
> First, why do you run firefix with sudo privilege?

Second, if you run **sudo firefox**, it will look at the Preferences of root's, not your account.

First Answer: At the beginning, I was trying to run firefox with preferences from another user (using "sudo -u otherUser"). Then I tried sudo without "-u" switch and you know the rest. Anyway, I just did it.

Second Answer: Are you sure? Why don't you try it? When you run firefox with sudo, firefox use YOUR profile.

(some minutes later..)

I think I get it. As I said, "sudo firefox" use your profile, and It set the ownership of the following files to root:
-Cache/
-bookmarks.bak
-bookmarks.html
-cookies.txt
-localstore.rdf
-prefs.js

Next time you run firefox without sudo, the application can't access this files and replace them with default ones.
I don't think this is wrong. What I don't understand is why ffox takes my profile path with sudo in the first time. Maybe it reads the path from an environment variable or something like that. What do you think?

---

