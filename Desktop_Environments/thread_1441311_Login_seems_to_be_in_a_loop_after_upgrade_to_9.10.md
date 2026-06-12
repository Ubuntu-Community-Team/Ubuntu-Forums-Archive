---
title: "Login seems to be in a loop after upgrade to 9.10"
date: 2010-03-28
forum: Desktop Environments
---

### Post by lostinUHF on 2010-03-28
I upgraded from 9.04 to 9.10 and everything seemed fine.   I and my family were all able to login just fine.  I also ran the update manager and updated various things such as open office etc.

Now I and my family try to login but end up coming back to the login screen again without seeing our Gnome desktop.  We do get the status bar after entering our credentials and it seems as though we will receive our desktop.  Then we get a black screen and then we are returned to the login screen.

Strangely enough I can always login as root and get a gnome desktop.  Sometimes I can login under my regular user and sometimes not.  Nobody else can login and receive a screen successfully.

I have run in recovery mode and the other ids can login just fine there.

I need some help as my system is not very usable right now.

---

### Post by lostinUHF on 2010-03-28
I have done some more looking around and have found the following errors in the authlog.  See sample below

Mar 28 16:10:51 mark-desktop gdm-session-worker[2661]: pam_unix(gdm:session): session opened for user debbie by (uid=0)

Mar 28 16:10:51 mark-desktop gdm-session-worker[2661]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :2

Mar 28 16:10:51 mark-desktop gnome-keyring-daemon[2690]: Couldn't unlock login keyring with provided password

Mar 28 16:10:51 mark-desktop gnome-keyring-daemon[2690]: Failed to unlock login on startup

Mar 28 16:10:54 mark-desktop seahorse-daemon[2774]: init gpgme version 1.1.8

Mar 28 16:11:03 mark-desktop gdm-session-worker[2661]: pam_unix(gdm:session): session closed for user debbie

Have seen other posts with inability to unlock the login keyring but none that are actually keeping anyone from logging in unless it is a default user.  I don't use default user.

---

### Post by Mantaraya on 2010-08-04
Sorry I can't provide you with the answer.
I just want to mention that I have the same problem and have not found a way to solve it so far.
What I do as a workaround. Is to start in a terminal than do su <user>  and than startx. This works ok for me but is obvious not the way is should work.

---

