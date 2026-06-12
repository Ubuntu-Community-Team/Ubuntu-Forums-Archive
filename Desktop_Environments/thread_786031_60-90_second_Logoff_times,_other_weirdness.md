---
title: "60-90 second Logoff times, other weirdness"
date: 2008-05-07
forum: Desktop Environments
---

### Post by quonsar on 2008-05-07
Under 8.04, I experience anywhere from 60 to 90 seconds of freeze after choosing Quit before the log off window appears (the one with the buttons to log off, restart, etc). This happens without fail. After experimenting a bit I find that the following error is always logged after I choose quit:
```
May  7 19:50:44 quonsar kernel: [ 1046.638289] nautilus[6178]: segfault at 2e000020 eip b76bd2d6 esp bf8c8f30 error 4
```

Additionally, I'm experiencing disappearing panel applets. When I re-add one that's turned invisible, there are suddenly two of them.

Can anyone help me troubleshoot this? This is an old Dell desktop thats been rock solid under previous Ubuntu versions.

---

### Post by Leslie Viljoen on 2008-05-09
I also have the logout wait and the segfault entry in /var/log/messages. 
This is after completing a full upgrade from Gutsy. 

I am on a Dell Inspiron laptop. 

Nautilus also seems to hang when accessing very specific Windows share paths. Other paths work fine, and it only hangs after accessing the folder for the second time!

---

