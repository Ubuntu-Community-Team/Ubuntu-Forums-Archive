---
title: "Cant Install Any New Programs"
date: 2006-05-21
forum: Desktop Environments
---

### Post by robcarr2 on 2006-05-21
Hey, well I installed Automatix and while it was installing the programs it comes with it froze on gstreamer, now whenever I try to install something I get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I have tried emptying the upgrade folder in dpkg and then I stop getting this error, however then it carrys on trying to install gstreamer, and then it just stops on gstreamer and doesnt install what I actually want to install.

Anyone have any idea how to fix this?

---

### Post by Sef on 2006-05-21
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Did you run 'dpkg --configure -a' (without the quotes)?

---

### Post by robcarr2 on 2006-05-21
OK i DID run that before I posted this thread and it didnt work, it still froze on gstreamer, but I just did it again and it fixed it. So I suppose my issue is resolved. Thanks for the reply :)

---

