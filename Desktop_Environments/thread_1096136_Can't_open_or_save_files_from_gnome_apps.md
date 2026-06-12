---
title: "Can't open or save files from gnome apps"
date: 2009-03-14
forum: Desktop Environments
---

### Post by jim h on 2009-03-14
Don't know how I caused this - lots happening including Nvidia card death, but since last week suddenly Firefox and Gimp simply halt when accessing a file menu.  So does gnome terminal if I try to edit profile.  Strace says they halt on a FUTEX_WAIT but I don't know enough to use that info.
  What confused me is that the logged in user has no problem.  But su to another user, you're dead (even root), tho command line file ops still work as always.  Found two similar posts but no real answers.
  A puzzle!  Any ideas what I broke? (Running Edgy.)  Thanks.

---

