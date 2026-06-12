---
title: "[SOLVED] Stupid Firefox mistake"
date: 2009-01-03
forum: General Help
---

### Post by Rog-Mahal on 2009-01-03
In an attempt to read the output of the 'tiger' security program, I ran firefox with sudo. (Yeah yeah, really dumb mistake). Now when I run Firefox normally I have no bookmarks and the browser behaves very oddly: Links don't work, username and password windows don't work. Running with sudo makes it work like normal. What did I do and how do I fix it?

---

### Post by Sef on 2009-01-03
Could you please explain how you fixed your system, so that others may benefit.   Thank you.

---

### Post by Rog-Mahal on 2009-01-04
My apologies. Running firefox as root changes the permissions of all its folders. To change them back to normal, simply run the following in terminal:

```
 sudo chown -R username:username ~/.mozilla
```

Where username is...your username. That will sort out the permissions problem.

---

