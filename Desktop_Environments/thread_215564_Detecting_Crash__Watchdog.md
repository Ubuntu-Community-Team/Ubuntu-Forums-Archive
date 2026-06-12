---
title: "Detecting Crash / Watchdog"
date: 2006-07-14
forum: Desktop Environments
---

### Post by s_g_robertson on 2006-07-14
Hello,

I'm not sure if what I am after is possible with an Ubuntu system but I thought I'd ask anyway.

I have a machine running as a server in my house that amongst other things runs mythtv.  At some point over the last couple of days it appears to have hung completely and as a result didn't record some programs.

Is there any method of detecting this type of crash and possibly notifying me or resetting the machine.  I can quite easily go a few days without using the server so it can take a while before I notice something has gone wrong.  To be fair this is the first time it has crashed and it has been running continuously for quite  a few weeks.

Thanks for any help.

Stephen.

---

### Post by mazirian on 2006-07-14
I won't be able to help you any beyond this, because I have never used what I am about to suggest, but djb's daemontools is a package that watches processes and, if they fail, attempts to restart them:

[http://cr.yp.to/daemontools.html](http://cr.yp.to/daemontools.html)

---

