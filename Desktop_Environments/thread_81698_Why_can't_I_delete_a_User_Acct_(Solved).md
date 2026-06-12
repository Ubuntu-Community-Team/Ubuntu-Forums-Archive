---
title: "Why can't I delete a User Acct???? (Solved)"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Georgie-o on 2005-10-25
I created a second user account useing the  System > Administration > Users and Groups.  However, when you try to delete it in the same fashion you end with a warning that all you can do is remove access, but not the files.  This can't be the case, correct?  I've read in a number of difffert places about "rm dir...sudo..." and whatever and tried them all.  Clearly the level of specificity needed to make the removal is difficult to communicate without screenshots and a clear understanding of what your logged in as and what directory your working in when trying to delete another.   I can't imagine that they made it so easy to set up a User Acct and so technical and difficult to delete one...??? ****

---

### Post by aysiu on 2005-10-25
I'm not sure what the deal is with that, but if you have to delete the files separately, it's not that hard to do. Let's say your user is cslewis. ```
sudo rm -r /home/cslewis
```

---

### Post by Georgie-o on 2005-10-25
you the man!


wow...directions that are clear...and work...

---

