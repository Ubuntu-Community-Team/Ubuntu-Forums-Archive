---
title: "Can only login as guest using Desktop after upgrade to 11.10"
date: 2012-08-13
forum: Desktop Environments
---

### Post by cthill on 2012-08-13
Hi,

I recently upgraded from Ubuntu 11.04 to 11.10, and I can now only login as Guest using the desktop. I cannot login with any normal account using the GUI - I get a blank screen for an instant and then I am returned directly to the login screen. I have tried a number of valid accounts on the system. I am able to login on the shell (CTRL+ALT+F1) with my username and password.

I have looked for solutions to this problem, but I have been unsuccessful. 

I do not have a .Xauthority file (which has been mentioned as a possible problem), instead I have a .ICEauthority file, which has the following ownership and permissions:
-rwxrwx--- 1 myuser myuser 176568 2012-08-09 12:50 .ICEauthority
(where I replaced my username with myuser).

I have reconfigured lightdm (dpkg-reconfigure lightdm) and selected lightdm, as suggested elsewhere, but this made no difference.

I've also checked the lightdm conf file to look for autologin lines, again as suggested elsewhere, but there were none.

In auth.log I can see the following message:
lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
but searching for these keywords have not produced helpful results.

My .xsession-errors file is empty.

Can anyone help please? This is causing me terrible stress as the PC is needed urgently. (I'm posting from an old laptop).

Thanks in advance,
CtHill

---

