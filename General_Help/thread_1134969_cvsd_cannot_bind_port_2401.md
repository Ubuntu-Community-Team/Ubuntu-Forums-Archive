---
title: "cvsd cannot bind port 2401"
date: 2009-04-24
forum: General Help
---

### Post by tepema on 2009-04-24
Hello, 

After upgrading to Jaunty Jackalope cvsd didn't work anymore. Only get "connection refused" message. No cvsd process running.

Everytime I tried to start service (etc/init.d/cvsd start) I get this error message in daemon.log

Apr 24 09:50:54 xx cvsd[4126]: version 1.0.16 bailing out
Apr 24 09:58:26 xx cvsd[4213]: version 1.0.16 starting
Apr 24 09:58:26 xx cvsd[4213]: listening on 0.0.0.0 2401
Apr 24 09:58:26 xx cvsd[4213]: bind() failed: Address already in use
Apr 24 09:58:26 xx cvsd[4213]: version 1.0.16 bailing out

I tried several ways to check out which process would listen port 2401 but couldn't find any. Also I tested port 2402 with same error. I tried to open port with iptables with no luck.

---

### Post by mehdic on 2009-05-04
The solution is posted here:
[http://ubuntuforums.org/showthread.php?p=7213962#post7213962](http://ubuntuforums.org/showthread.php?p=7213962#post7213962)

---

