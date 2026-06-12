---
title: "Simple Problem: packager manager problem"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by unshareef on 2008-02-01
Hi,

I have gutsy and I wanted some new games.

So I went to Applications>Add/Remove and selected all the games I wanted and an error came up saying: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running dpkg --configure -a in terminal and it said that I need "superuser" privelage. I dont know what that is.

Why is this?

Can anyone help?

Many thanks.

---

### Post by trehoffman on 2008-02-01
Try "sudo dpkg --configure -a"

---

