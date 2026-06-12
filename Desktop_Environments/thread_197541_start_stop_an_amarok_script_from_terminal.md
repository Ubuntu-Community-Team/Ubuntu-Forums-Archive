---
title: "start stop an amarok script from terminal"
date: 2006-06-15
forum: Desktop Environments
---

### Post by harty83 on 2006-06-15
I was wondering if anyone knew if it was possible to start an amarok script from the terminal while amarok is running.  

I want to run an icecast server with the icecast script for amarok.  I have everything configured and running fine.  But I would like to not have the script running unless I am streaming so I want to set it up (if possible) to where I can run and stop the script remotely (via a ssh terminal or something).

Thanks!

---

### Post by asimon on 2006-06-16
You can do it via dcop, i.e. something like
```

dcop amarok script runScript "PlaylistServer.py"
```
for starting and ```

dcop amarok script stopScript "PlaylistServer.py"

``` for stopping.

You can start 'kdcop' to explore what other things you can do with dcop.

---

