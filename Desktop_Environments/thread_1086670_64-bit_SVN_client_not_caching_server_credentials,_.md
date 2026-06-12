---
title: "64-bit SVN client not caching server credentials, but 32-bit is."
date: 2009-03-04
forum: Desktop Environments
---

### Post by GeekLove_JavaStyle on 2009-03-04
Hello All,
Something very odd is happening on my desktop.  I run Ubuntu 32-bit at home and work and subversion behaves very consistently.  I check out a project using 

```
svn co ${URL} ${LOCAL_PATH} --username ${UN} --password ${PW}
```

...and then I can execute ...

```
svn update *
```

...and it remembers my credentials.  

I upgraded to 64-bit Ubuntu (8.10) at home and now SVN never remembers my credentials.  I tried checking ~/.subversion/auth/svn.simple/* and can see that it's saving the values for the servers, but apparently not using them.  

Is there a switch that'll fix this?  

My 32-bit work computer is still caching credentials properly and is updated to the same version.

Does anyone have any advice?

Thanks in advance,
Steven

---

