---
title: "Can't login to Desktop"
date: 2012-09-09
forum: Desktop Environments
---

### Post by Geffers on 2012-09-09
Strange, this morning I seem unable to use the boot up user window to login.

I enter my password, screen goes blank, see a few commands which show too briefly to read then I get the user login window again.

I can logon as guest, also using Ctrl-Alt-F1 I can log on using my normal username and password.

Any ideas what might be the problem.

Geffers

---

### Post by zombifier25 on 2012-09-09
> **zombifier25 said:**
> Someone should really file a bug report, since for such an uncommon problem many people are having it.
Login in your terminal and type this command:
```
sudo chown yourusername:yourusername ~/.Xauthority 
```

I'm a little lazy :P

---

### Post by Geffers on 2012-09-09
Thanks very much, that worked.

Geffers

---

