---
title: "ksmserverrc not writable?"
date: 2010-02-26
forum: Desktop Environments
---

### Post by h4x0rmx on 2010-02-26
I just installed KDE SC 4.4 on Ubuntu 9.10 successfully after a couple of tries.  When I tried to login for the first time I received this message:
'Configuration file "/home/user/.kde/share/config/ksmserverrc" not writable. Please contact your system administrator'

I'm guessing that it has to do with the permissions, but how do I solve it?
Please be as explicit as you can. I'll appreciate it!

---

### Post by h4x0rmx on 2010-02-26
I got it fixed, just in case someone has the same problem:

$ sudo chown -R user:user /home/user

---

