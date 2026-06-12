---
title: "New Intrepid install hangs"
date: 2009-03-22
forum: General Help
---

### Post by dcroxton on 2009-03-22
I installed Intrepid on a spare partition.  When it boots up, it gets through the part with the Ubuntu logo and progress bar, but then hangs.  The screen is completely blank except for the "wait" cursor.

I have very little idea where to look for the problem.  I can't find anything in the logs, but, then, I don't really know what to look for.  Here are the contents of /var/log/gdm/:0.log, which at least seems to indicate some problem:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux dcroxton-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 20 20:02:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
AUDIT: Fri Mar 20 20:02:32 2009: 4984 X: client 4 rejected from local host ( uid=0 gid=0 pid=5189 )
AUDIT: Fri Mar 20 20:02:41 2009: 4984 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5194 )
AUDIT: Fri Mar 20 20:02:41 2009: 4984 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5195 )
AUDIT: Fri Mar 20 20:02:41 2009: 4984 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5196 )

```

I can post whatever other information is necessary, I just don't have a clue where to go from here.

Sincerely,
Derek

---

