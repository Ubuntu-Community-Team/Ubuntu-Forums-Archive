---
title: "Bug in User Admin GUI?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by crokett on 2006-10-07
Had a scare when sudo quit working and root password did not work.  Thought I was hacked but I didn't see how. Checked the auth log file and all I could see was me running the Users and Groups admin util to add my wife's account to a group. There was a lot of stuff logged it shouldn't have done - such as resetting root password and resetting the password of some of the other system accounts.  It also did the actual addition in an odd way - removed me from the group then added me and my wife back.  As I recall the same symptoms happened a few weeks ago when I made the exact same change.  Had to reinstall then because of unrelated issues.  

This time I added myself back to admin group from the command line and all works again.  Is there a way to search for a bug?  Or report one?  The admin tool shouldn't be modifying other users when performing an operation.  And certainly not root.

---

### Post by crokett on 2006-10-08
I reported the bug.  I am going to stick with command line user admin for a while.  The admin tool is doing a lot of things it should not do.

---

