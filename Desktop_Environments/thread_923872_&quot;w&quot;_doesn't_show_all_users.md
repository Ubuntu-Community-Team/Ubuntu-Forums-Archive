---
title: "&quot;w&quot; doesn't show all users"
date: 2008-09-18
forum: Desktop Environments
---

### Post by sir_blargh on 2008-09-18
```
(scott) blargh-desktop:~/build/xmms-1.2.11/xmms
568 -> w
 20:46:58 up 59 days, 15:27,  **4 users**,  load average: 0.29, 0.34, 0.29
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
scott    tty1     -                16:50    3:56   0.00s  0.00s -bash
scott    tty9     :0               16:50    0.00s  8:55m  0.10s x-session-manager
scott    pts/0    :0.0             16:56    0.00s  0.08s  5.60s gnome-terminal

```

It says 4 users, but then lists only 3.  Then there's this:

```
(scott) blargh-desktop:~/build/xmms-1.2.11/xmms
571 -> last | grep 'still logged in'
scott    pts/0        :0.0             Thu Sep 18 16:56   still logged in   
scott    tty9         :0               Thu Sep 18 16:50   still logged in   
scott    tty1                          Thu Sep 18 16:50   still logged in   

```

Any idea where the missing user is?

---

