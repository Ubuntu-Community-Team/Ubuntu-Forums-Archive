---
title: "SOMETHING messes with access rights"
date: 2006-09-20
forum: Desktop Environments
---

### Post by lfys on 2006-09-20
SOMETHING messed with the access rights to a partition of which I am "the owner". 

Out of the blue this SOMETHING has, in the last 24 hours, twice blocked writing to a complete partition although at first sight nothing seems wrong (077), and this for no obvious reason. The third time not the partition as a whole was unwritable but ALL the directories within it!

This behaviour makes me worried.

***************************

OOPS. IT DID IT AGAIN AFTER COMING OUT OF SUSPEND MODE.

***************************

Mmmm .... . Logging off and back on in Gnome seems to take the problem away ... :confused:

***************************

And then again NO. Now I can fix the lock only with a complete restart.

---

### Post by lfys on 2006-11-16
Problem solved.
Firefox & Thunderbird generated write errors on fat32-partition. Access rights were taken away.

Made FF & TB profiles in my home folder.

---

