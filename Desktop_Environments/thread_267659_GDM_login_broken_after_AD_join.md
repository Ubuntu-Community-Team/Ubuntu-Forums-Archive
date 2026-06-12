---
title: "GDM login broken after AD join"
date: 2006-09-28
forum: Desktop Environments
---

### Post by genesis[OFT] on 2006-09-28
Hi guys, New on the Ubuntu Forums!  Just wanted to say that all you guys have done an AWESOME job with this distro..hats off to all the devs and Mr. Mark Shuttleworth, the project leader :D

Now, to my problem.  I've recently successfully joined my Windows 2003 Server AD Domain on Ubuntu Dapper Drake 6.06 LTS and I can login locally and remotely via NX and SSH with AD accounts.  'wbinfo -u', 'wbinfo -g', 'getent passwd' and 'getent group' all work sucessfully.

The only problem I'm having is logging in under local users - that is, users on the Ubuntu box.  I type in the username and password, and while it logs in, a huge chunk of errors pop up saying can't authenticate to this and that, and GDM starts....but without a theme or any top\bottom bars.

I imagine the reason for this is that the files in /etc/pam.d allow only for domain logins now that I've got it working, and when I decide to use a local user account, it doesn't work.  Funnily enough, I'm able to login with both AD users and local users in a terminal, just logging in under local users in GDM, causes all these errors to pop up.

Any ideas on what could be causing this problem? :-k

---

### Post by genesis[OFT] on 2006-09-30
*bump*

Please...anyone?  I need an answer... :D

---

