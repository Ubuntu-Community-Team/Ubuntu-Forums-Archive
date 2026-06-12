---
title: "Can't Login all of a sudden"
date: 2006-09-28
forum: Desktop Environments
---

### Post by bgullicksen on 2006-09-28
I am running Ubuntu 6.0.6 and it has been working great for weeks.  All of a sudden this morning, I can no longer login using any account.  

The system boots to run level 5 and at the graphical login, I can enter the username and password.  Then the screen turns black and for a second you see the typical non-graphical login prompt and then you are returned to the graphical login prompt.

I can ssh to the box and connect with my user just fine, so it seems to be a problem with the x session???

Any thoughts?

-Bill Gullicksen

---

### Post by bgullicksen on 2006-09-28
Problem solved.  The root file system ran out of available disk space.  I deleted some junk and everything is back to normal.

Thanks!

---

