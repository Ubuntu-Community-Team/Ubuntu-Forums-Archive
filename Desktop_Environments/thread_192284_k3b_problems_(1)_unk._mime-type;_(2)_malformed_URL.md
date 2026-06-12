---
title: "k3b problems: (1) unk. mime-type; (2) malformed URL"
date: 2006-06-08
forum: Desktop Environments
---

### Post by jonrkc on 2006-06-08
I installed Xubuntu Dapper 6.06 from the ISO (burned to CD).  When I try to run k3b to see if I can burn DVD's and CD's under Dapper, I was getting error messages about an unknown mime-type, "octet-stream."  With help of Google, I solved that by adding this line in /etc/mailcap and also in ~/.mailcap files:
```

application/octet-stream ; octet-stream

```
I hope this helps somebody with a similar problem.

A second problem with k3b I have not been able to solve: I always get "Malformed URL: file:///home/jon/Desktop" error message followed by immediate crash.  (I'm also getting this group of messages:
```
Warning: connect() failed: : Permission denied
KCrash cannot reach kdeinit, launching directly.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
qstring_to_xtp result code -2

```...but until I solve the "malformed URL" problem I won't know if they are of any significance--or will still occur.)

With Google I've found many instances of "malformed URL" mostly in connection with mail services.  I haven't seen any solution put forward, so far.

Does anybody have some ideas on solving this?

By the way, even if I try to start k3b this way:
```

kdeinit ; k3b &

```
which worked under Hoary 5.04, I still get the crash.

---

