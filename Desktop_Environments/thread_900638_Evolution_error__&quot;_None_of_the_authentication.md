---
title: "Evolution error:  &quot; None of the authentication protocols specified are supported&quot;"
date: 2008-08-25
forum: Desktop Environments
---

### Post by tgiguiere on 2008-08-25
Hello. I am having a problem trying to start evolution logged in as a normal, non-root user. 

here is the message:
```

(evolution:20476): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Aborted

```

I can start evolution as root, however. 

Any ideas what the problem is?

Thanks.

---

### Post by Pyrrhias on 2008-08-26
I have the same problem with gedit :

n$ gedit

(gedit:8847): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
/home/.esd_auth: Permission denied
/home/.esd_auth: Permission denied

With sudo gedit it works well.
When I do ps.....
allain@allain-laptop:~/allain$ ps aux | grep gnome-session
allain    8909  0.0  0.1   3004   760 pts/1    R+   09:22   0:00 grep gnome-session

Someone have an idea to solve this problem?



Thanks

---

