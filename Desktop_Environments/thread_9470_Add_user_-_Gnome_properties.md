---
title: "Add user - Gnome properties?"
date: 2004-12-29
forum: Desktop Environments
---

### Post by mjjohansen on 2004-12-29
I have looked for this issue, but can't seem to find it mentioned.
I have tried adding a user.
I use the lovely Gnome on Warty. When I add the new user, the login session fails, since it can't create the Gnome folders in the new user's home folder. I have tried creating a couple of the missing ones, but that is a kludge and not much of a solution.
Any pointers?

---

### Post by p!=f on 2004-12-29
```

sudo adduser foo

```
Check permissions on the user home directory.

---

### Post by mjjohansen on 2004-12-31
This worked as it should. It just confused me that the user administration GUI did not create all the necessary files, while the command line option did.

---

