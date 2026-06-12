---
title: "MAIL environment variable set wrong"
date: 2009-05-29
forum: General Help
---

### Post by david00 on 2009-05-29
Hi,

I am using Ubuntu Hardy x86_64.  The problem I have is that whenever I log in, the MAIL environment variable is set to '/var/mail/david' (where my username is 'david').  This isn't right, since I don't keep my mail in Mbox under /var/mail.  In fact, on this machine I don't get mail for my local username, and I'd like MAIL to be unset when I log in.

```
david@scatha $ echo $MAIL
/var/mail/david
```I've tried to find out where this gets set, and I've found that it's set by PAM.  However, PAM is fairly obscure.  The PAM module responsible for setting the variable seems to be 'pam_mail'.  There are a few lines in various files under /etc/pam.d that seem to enable this module:

```
david@scatha $ grep -r pam_mail /etc/pam.d
/etc/pam.d/login:session    optional   pam_mail.so standard
/etc/pam.d/sshd:session    optional     pam_mail.so standard noenv # [1]
/etc/pam.d/su:session    optional   pam_mail.so nopen
```However, commenting out all these lines doesn't seem to solve the problem.  (Since I log in by ssh, I restarted sshd to apply the changes.)  Neither does appending 'noenv' to all lines, as "man pam_mail" suggests that it should.  MAIL is still set in all circumstances - this includes non-SSH physical logins.

There's also some related things in /etc/login.defs, albeit with the following note:

```
# NOTE: This is no more used for setting up users MAIL environment variable
#       which is, starting from shadow 4.0.12-1 in Debian, entirely the
#       job of the pam_mail PAM modules
#       See default PAM configuration files provided for
#       login, su, etc.
```Why do I care?  Because I use zsh, which has a feature to automatically check for mail when MAIL is defined.

> MAIL: If this parameter is set and mailpath is not set, the shell looks for mail in the specified file.  There's no way to disable this check, so (since /var/mail is forbidden to my user), every five minutes I get a message "/var/mail/david: permission denied".  I know how to work around this in many ways: unset MAIL in my zshrc, profile, /etc/profile; change the permissions on /var/mail.  But none of these do exactly what I want, which is to avoid setting MAIL in the first place.  Ideally the 'noenv' option should do this perfectly, but it doesn't seem to work.

Any idea where I'm going wrong?

---

