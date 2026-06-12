---
title: "Managing Users"
date: 2009-04-29
forum: General Help
---

### Post by acute_archer on 2009-04-29
I'm new to Ubuntu and I'm running 8.10. I added a user just to practice and I can't figure out why with only minimal permissions they can still view documents, pictures, etc.. on the initial (admin) account. I've search high and low but couldn't find an answer. Is this normal or have I missed something?

---

### Post by taurus on 2009-04-29
Do you mean the second user is able to view files that belong to the original user?  Just change the permissions if you don't want anybody to view stuff in your $HOME.  _Assuming_ john is the username that you don't want anybody to access, log in as john and run

```
chmod 700 /home/john
```

---

### Post by Brandon Williams on 2009-04-29
The default umask in Ubuntu (most flavors of linux, actually) is 022, which means that the default permissions on new files allow any user to read the files (and execute them, if they are executable). If you don't want other users to be able to read your files, then you can either change the permissions on them after creation, or set your you umask to something more restrictive. I typically use 077 on multi-user systems so that I must explicitly give other users read, write, and/or execute permission for files when I create them.

---

### Post by acute_archer on 2009-04-30
Thanks for the info. It took a little research to find out the numbers you guys were referring to, but I think I'm on my way to figuring it out.Thanks again.

---

### Post by _Purple_ on 2009-04-30
> **acute_archer said:**
> Thanks for the info. It took a little research to find out the numbers you guys were referring to, but I think I'm on my way to figuring it out.Thanks again.

You can check this link to learn more about permissions

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

