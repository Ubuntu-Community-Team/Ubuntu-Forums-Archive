---
title: "Security?!?!"
date: 2005-09-14
forum: Desktop Environments
---

### Post by zappa86 on 2005-09-14
I did a netstat -l to see what was opened on my system and I found several entries 
like:
unix  2      [ ACC ]     STREAM     LISTENING     13734   /tmp/orbit-harry/linc-226f-0-1bac2d62a9d22

and

unix  2      [ ACC ]     STREAM     LISTENING     13186    @/tmp/dbus-hIk2dV0DVj

I'm somewhat new to linux, however in windows I know that programs in the tmp directory that look that that can be problems? is this normal or do I have a virus or worm or something?

---

### Post by cwaldbieser on 2005-09-14
[QUOTE=zappa86]I did a netstat -l to see what was opened on my system and I found several entries 
like:
unix  2      [ ACC ]     STREAM     LISTENING     13734   /tmp/orbit-harry/linc-226f-0-1bac2d62a9d22

and

unix  2      [ ACC ]     STREAM     LISTENING     13186    @/tmp/dbus-hIk2dV0DVj

I'm somewhat new to linux, however in windows I know that programs in the tmp directory that look that that can be problems? is this normal or do I have a virus or worm or something?[/QUOTE]
It is normal UNIX domain socket stuff.  Try using the -t or -u flags to see just TCP or UDP connections.

---

### Post by zappa86 on 2005-09-14
Alright. Thanks. I feel much better now :)

---

