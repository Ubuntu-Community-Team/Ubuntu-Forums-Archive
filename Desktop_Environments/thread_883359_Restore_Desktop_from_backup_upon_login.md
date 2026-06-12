---
title: "Restore Desktop from backup upon login"
date: 2008-08-07
forum: Desktop Environments
---

### Post by mikerobinson on 2008-08-07
I am running kubuntu. I have been trying to get a script so that when a user logs in, it will restore their Desktop from a file storage. This is the user's ~/.xsession file:

```
#!/bin/sh
rm -r /home/english/Desktop
cd /home/Desktop-bak
cp -R ./ /home/english/Desktop
```

The script executes fine and it works, however the X session crashes right after its execution. What here would cause the session to crash and how can I get around it?

---

### Post by mikerobinson on 2008-08-08
I just realized that this happens with ANY .xsession file. I just created an empty file and when the user starts KDE with that session, it just goes back to the login screen. Should I file a bug report? Can anyone else confirm this?

---

### Post by txcrackers on 2008-08-09
It's doing this because you don't *quite* have it right...

Try *man Xsession* and *man xinit* - these man pages specifically talk about the X initialization process and how .xsession fits into it.

---

### Post by yinsh on 2008-08-09
I'm as new as can be to linux and after seeing this topic I became intrigued.  I'm running ubuntu and am wondering if there is a similar process by which the desktop and all its contents will reload upon startup

---

