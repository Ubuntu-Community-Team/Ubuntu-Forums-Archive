---
title: "R620 crash with 12.04"
date: 2012-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dellneo on 2012-07-09
We just bought two R620.
Unfortunately they crash (reboot) when installing the recent 12.04 Server 64bit
(ubuntu-12.04-server-amd64.iso)
(and after that the idrac-logfile says:"CPU 2 has an internal error (IERR)." )

A 32bit-kernel boots, but freezes when transferring data over the net.

I can reproduce the behaviour on both the machines we got. 

Can anyone give a hint? I cannot believe that both machines have a hardware-problem.

nd

---

### Post by macindy on 2012-09-01
Think we have the quite same problem. I have installed also Ubuntu 12.04 LTS on our new 9G Dell R420 server. Under load the CPUs asserts IERR error.

I phoned with Dell, the dell technician told me, it is not a hardware error. I also think so, because the IERR errors happens on both server, always they get load.

I read something, the driver could cause this. How to get an idea, what could be the cause?
And by the way: How could I reset the IERR error, so my dell machine doesn't show me it all the time?

---

### Post by deltaprojects on 2012-09-16
Check this thread also, discusses model R720 with the exact same problem - and it presents a temporary work around.

[http://ubuntuforums.org/showthread.php?t=2053947](http://ubuntuforums.org/showthread.php?t=2053947)

---

