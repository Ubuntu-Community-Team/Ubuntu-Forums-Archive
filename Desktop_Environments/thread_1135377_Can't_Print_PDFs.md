---
title: "Can't Print PDFs"
date: 2009-04-24
forum: Desktop Environments
---

### Post by infinitezero on 2009-04-24
Every time I go to print a PDF the application just hangs then terminates. I have this issue on all PDF viewers that I have tried, any thoughts?

Kubuntu 9.04

Thanks,
iz

---

### Post by infinitezero on 2009-04-24
Is anyone else experiencing this?

---

### Post by infinitezero on 2009-04-25
Update-
I can print PDFs as root just fine but not under any normal user accounts. It sounds like a permission issue but I don't see anything wrong with the permissions.



iz


Solved:
For some reason my profiles did not have the group "users" added to them.

---

### Post by Turtle.net on 2009-04-25
I experience the same problem on a clean new install of 9.04 Ubuntu

---

### Post by Cuba71 on 2009-04-26
I installed Adobe Reader 9 and can print without problems

---

### Post by ssdt on 2009-04-26
Yeah no problem with Adobe Reader.

---

### Post by infinitezero on 2009-04-27
This is strange, now for some reason I can't print again. This time all of my applications freeze then crash when I go to print.

 iz


Whatever the cups update was it **_seems_** to have taken care of the issue.

---

### Post by kstarkey1 on 2009-06-09
> **infinitezero said:**
> Update-
...

Solved:
For some reason my profiles did not have the group "users" added to them.

Thanks so much infinitezero!  I missed this 'Solved' part the first time I found this thread.  I've been working on this problem for days.  I was minutes away from going back to Hardy, but was dreading all of the work involved with that

If you found this thread because you're having issues printing pdfs in Jaunty (like me and apparently many others), go to System > Administration > Users and Groups and click unlock, enter your password, then click'Manage Groups'.  From there select 'users' on the left then click the Properties button on the right.  Under 'Group Members' make sure there's a check next to your name.  Now I have no issues printing pdfs, just like the good old days :)

---

