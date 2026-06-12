---
title: "Dovecot IMAP remote connection problems"
date: 2006-07-13
forum: Desktop Environments
---

### Post by marcndd on 2006-07-13
I have dovecot configured as an IMAP server, and connect to it with email clients locally and remotely.  I have done this without a problem on Breezy, and I am pretty sure (but not positive) it worked initially when I upgraded to Dapper.  I noticed a couple of dovecot updates since then.

I normally just do email with an email client locally on the Ubuntu desktop, so I don't know exactly when this problem started.  What I do know is that now whenever I try to connect from a remote system my email client says something to the effect that "logins are disabled on the server and maybe I need to enable SSL or TLS authentication".  I am using plaintext authentication.  If it matters my email client on all systems is Seamonkey, which is basically the same as Mozilla or Thunderbird.

I am pretty sure I am not running a firewall (IP Chains or whatever) on the system (unless the Dapper upgrade slipped one in), as I am behind a NAT router.  Connecting from the local system still works, which is what is so weird, it is only connections from remote systems that have the problem.  And it worked from remote systems until recently.

I looked through the /etc/dovecot/dovecot.conf file and didn't see anything that looked too suspicious, although I manually set the maximum number of simultaneous connections allowed to be sure it allows several.  (I almost always leave the local email client running).  I did try shutting down the local email client, but the remote still couldn't connect.

The system is up-to-date, there are no dovecot updates available.  I Googled and searched the forum, and didn't see anything.

Any ideas?

---

