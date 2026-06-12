---
title: "How do u allow SSH or telnet into your server to allow command line access remotely?"
date: 2009-01-27
forum: General Help
---

### Post by Linuxwho? on 2009-01-27
I want to be able to putty into the command prompt of my non-gui based linux.  How do I do that?

---

### Post by icheyne on 2009-01-28
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by sedawk on 2009-01-28
Basic ssh access should work out of the box after installing the software
package "openssh-server".

(After installation the process "sshd" should be running, you can
 check the process id with "pgrep sshd" from command line).

---

