---
title: "yohoho puzzle pirates runs under one user, but not another"
date: 2006-07-15
forum: Desktop Environments
---

### Post by jjf on 2006-07-15
My wife loves Puzzle Pirates.  I installed under my user (who as an "admin" has sudo access) and it works fine.  I seem to remember that I had to set Sun Java as my default version in order for it to work.

I ran the install script under my wife's account (who as a "user" is not a sudoer), but Puzzle Pirates won't launch.  She has "execute" privilege on the .sh script.  I can switch over to my account and it launches fine.  

Any ideas what might be wrong?

---

### Post by christhemonkey on 2006-07-15
Where did it install to?
She may not have the permissions to use it with her account.

---

### Post by jjf on 2006-07-15
It installed to her home directory:

/home/elisa/yohoho/

so she should have privilege to access it.  Maybe she doesn't have privileges to use some other config file it depends on???

---

