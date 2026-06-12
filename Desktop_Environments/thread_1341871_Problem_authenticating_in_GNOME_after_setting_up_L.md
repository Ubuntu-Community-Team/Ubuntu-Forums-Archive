---
title: "Problem authenticating in GNOME after setting up LDAP"
date: 2009-11-30
forum: Desktop Environments
---

### Post by larseko on 2009-11-30
Hi.

I'm setting up a new disk image for our student PCs, with the new Karmic Koala. I've succeeded in getting LDAP to work like before, with libnss and libpam + autofs/NFS, but I have a strange problem when logging into the admin account (the one I've set up locally when I installed ubuntu). 

After I set up LDAP, I'm no longer able to start administrative tasks while logged in as the local admin. The app will ask me to enter password for administrative tasks, but when I do, it just pops back up with a new password prompt.

In syslog, I get the following error:

Nov 30 12:47:34 vust1-3 kernel: [ 1893.866653] polkit-agent-he[3826]: segfault at 4 ip 00b36b90 sp bfc56130 error 4 in libpam.so.0.82.1[b33000+b000]

So I guess it is something about policykit and libpam. Anyone got any ideas as to what might be wrong?

Thanks, would be great to get people up and running on Karmic, at it's a great improvement in many regards.

---

### Post by sedawk on 2009-11-30
Hello!

This segfault isn't good. But anyway:

* Is the admin user still local (in /etc/passwd) or 
  migrated to LDAP?
* is "passwd" in nsswitch.conf using "files" keyword before ldap?
* Any files you edited manually (syntax errors, etc).
* Did you take all the extra software from karmic's official
  repository?
* Can you successfully login with any LDAP account?
  (or see proper output when running "id <user-in-ldap>" )

---

### Post by larseko on 2009-11-30
Thank you for your elaborate response.

First, I have to modify the scenario a bit. The problem does not appear when I start an administrative app that needs authentication right away, it only happens when there's an app with an "unlock" feature. Like the login screen settings app or the "users and groups" app. 

For your followup questions:

* The administrator is local. There is no administrator account in the LDAP directory.
* Yes, "files" is before "ldap". (Didn't work too well the other way around.)
* I have not edited any files manually, as I use puppet/puppetmaster to manage configuration files. These are the same files as I use (successfully) on the other Hardy workstations. 
* Yes.
* Yes.

:-)

---

### Post by larseko on 2009-12-08
I'll bump this... still struggling. Could it be a policykit bug? Am I the only one experiencing it?

---

### Post by larseko on 2010-06-16
Another bump. This also happens in Lucid. Noone else has experienced this?

---

### Post by dhufish on 2010-12-10
bump!

Using 10.10, I have just setup LDAP Samba PDC and now I can't login to Gnome with any accounts... My admin account (mike) is a pam account.  I have also created a new LDAP account with also fails to successfully login to gnome.  Both return to the login page.

From /var/log/auth.log
```
Dec 11 12:30:40 ahong gdm-session-worker[3383]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "mike"
Dec 11 12:30:44 ahong gdm-session-worker[3383]: pam_unix(gdm:session): session opened for user mike by (uid=0)
Dec 11 12:30:44 ahong gdm-session-worker[3383]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Dec 11 12:30:44 ahong gdm-session-worker[3383]: pam_unix(gdm:session): session closed for user mike

```

Any ideas?

---

### Post by eti.que on 2011-01-06
Exactly the same problem here as you, dhufish. Authenticating against a LDAP server and I cannot login with my accounts (same error as you) though:
- login through SSH works
- login through nomachine (which is based on SSH anyway) works
- autologin works

Any clue ?

Cheers!

---

### Post by FiVAL on 2011-10-19
Bump..

I have also Xact the same problem.
Does one of U already found they answer??

---

### Post by larseko on 2011-10-19
Sorry, but I've given up on LDAP.

---

