---
title: "unable to change gksu to gksudo in applications:///"
date: 2004-12-15
forum: Desktop Environments
---

### Post by marwal on 2004-12-15
Hi

I try to change firestarter starter from "gksu /usr/sbin/firestarter" to "gksudo /usr/sbin/firestarter".

I can make the change and start firestarter but the string is then reset to the original value.

I've changed it both as mainuser and as root.
I've changed it by 

1) right-clicking on Firestarter Properties in Program menu 
2) by running nautilus applications:/// and change the Starter line.

What am I doing wrong here?  :?

---

### Post by jdong on 2004-12-16
It sticks pretty well for me....

Anyway, as soon as we get a 1.0.1 release of Firestarter in Hoary or Debian Sid, I'm gonna backport it to Warty and fix the fricking launcher FOR GOOD. :D

---

### Post by marwal on 2004-12-16
Deleting the starterlink and creating a new one instead of altering the old, solved the problem.

On trashing the old link:
"Unable to put this in wastebasked - do you want to delete it permanently?" (translated from swedish).

---

