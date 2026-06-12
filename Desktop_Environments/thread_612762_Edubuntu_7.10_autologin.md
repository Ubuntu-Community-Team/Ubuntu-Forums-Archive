---
title: "Edubuntu 7.10 autologin"
date: 2007-11-14
forum: Desktop Environments
---

### Post by cmddotexe on 2007-11-14
Hi,

Does anyone have any tips for getting autologin working for Edubuntu 7.10 thin clients?

I have a thin client environment set up for testing, and everything works fine when autologin isn't configured. The thin client boots up, gets to the logon screen and I can log in manually without a problem.

When I edit /var/lib/tftpboot/ltsp/i386/lts.conf and add the following:

[01:02:03:04:05:06]
 LDM_USERNAME=user
 LDM_PASSWORD=password

(where 01:02:03:04:05:06 is the thin clients mac address), the client gets as far as a black screen with an 'X' cursor and goes no further. Nothing appears in the auth.log on the server.

Presumably it's not a display configuration issue, as when I comment out the two LDM_* lines and reboot, everything works fine and I can log in manually from the client using the credentials specified in lts.conf.

Any suggestions?

Thanks.

---

