---
title: "Xnest Problem Starting Remote Session"
date: 2006-06-12
forum: Desktop Environments
---

### Post by limewolf on 2006-06-12
When I try to use Xnest to start a remote x session on my dapper machine I get the following error, after I have completed the login:

```

error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
FreeFontPath: FPE "/usr/share/X11/fonts/misc/" refcount is 2, should be 1; fixing.
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
X connection to :0.0 broken (explicit kill or server shutdown).

```



The remote machine is a sun box running CDE. I can use it remotely via Exceed under windows ok. On first starting Xnest, I do get a window opening and I can enter my username and password (just like with exceed) but after this CDE fails to start and I get the above error. Can anyone suggest what it might be, seems to suggest it is a problem with my dapper machine (the missing SecurityPolicy file)?

*Update:* Just as I am writing this I've tried using Xephyr instead and that has worked without a problem - I can login and use the machine without problems. Though I'm still abit puzzled by the above error with Xnest.

---

