---
title: "krfb issues"
date: 2008-09-11
forum: Desktop Environments
---

### Post by cnganesh on 2008-09-11
Hi,

I am having some trouble connecting to a kubuntu based desktop running krfb through a vnc client (realvnc) on windows xp.

When I try to connect to the server, it shows me the password window (meaning it was able to connect to the server), but on entering the correct password, gives me:

"Unknown security result from server.  Do you wish to attempt to reconnect to <host> ?"

I can see that the krfb process is spawned on the server.

$ ps -ef | grep krfb
13369  6681  1 00:39 ?        00:00:00 krfb --kinetd 12

I tried killing the krfb process and trying again, but of no avail.  I also tried with tightvnc client, but that also asks for the password but fails to bring up the desktop.

Has anybody faced a similar issue ?  Any help appreciated. I also cant seem to find krfb logs anywhere.  Does anybody know how to get krfb logs ?

Thanks,
Gan

---

