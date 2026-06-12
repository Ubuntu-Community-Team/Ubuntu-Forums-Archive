---
title: "VPN to Windows with pptp-linux error"
date: 2005-12-16
forum: General Help
---

### Post by byteshack on 2005-12-16
Hello all,

I have been trying to connect to my company's VPN through Linux.  I need to use rdesktop to a machine at work, but the only way to connect to anything inside is by using vpn.  I have read and follow most everything I could find on pptp for ubuntu or debian.  I have also installed pptpconfig to make me a bit lazy :)

When I try to connect to my machine, I get:

Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
Unknown MS-CHAP authentication failure: E=691 R=1 C=***** V=3
Connection terminated.
pptpconfig: pppd process terminated by signal 19 (failed)
pptpconfig: SIGSTOP


Any help would be greatly appreciated.  Docos seem to point to 691 as being a username/password error.  My password has a space in it, does any one know if that is a problem?

Thanks!
Daniel

---

### Post by byteshack on 2006-05-20
Just in case anyone finds this thread because they have a similar issue.  My problem was that there was a space in my password.  Try changing that and it might solve your problems.

---

