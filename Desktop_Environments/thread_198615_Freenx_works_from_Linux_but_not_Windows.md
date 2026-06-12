---
title: "Freenx works from Linux but not Windows"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Kosh42 on 2006-06-17
Well, after a day and a half of Google research and some messing about, I have the Freenx server running perfectly on my Ubuntu box. If I run the client on localhost, works a dream.

Proplem starts when I try to connect from the Windows client. nxserverlog has this to say on the subject:

```
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1004 Error: nxagent failed to start with: NXAGENT: Fatal IO error on display "nx/nx,options=/home/tim/.nx/C-STATION-1000-455D66F7DAD50E42B23DB89184617E7F/options:1000".
NX> 504 Session startup failed.
NX> 1001 Bye.
```

Only odd thing is that I cannot see a "C-STATION-1000-..." in my home directory, only a "S-STATION-1000-..." but I have a feeling this is not the problem.

Any ideas?

Thanks,

Tim

---

### Post by Kosh42 on 2006-06-18
Update: I tried this from a different PC and it worked a dream, both directly with the client and also wia a webpage with NX Web Companion. Seems this is limited to some Windows clients, rather than being a server problem.

For reference, the Windows machine that worked used 2000 Professional, the one that didn't is running XP x64 Professional.

---

