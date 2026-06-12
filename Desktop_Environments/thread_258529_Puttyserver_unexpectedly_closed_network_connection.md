---
title: "Putty:server unexpectedly closed network connection"
date: 2006-09-16
forum: Desktop Environments
---

### Post by hraposo on 2006-09-16
I intalled putty. when I try acess to another macine I receive the message of putty ```
server unexpectedly closed network connection
```. When I do ssh -X 192.168.1.4 the output is ```

Read from socket failed: Connection reset by peer
``` So, maybe the problem is in SSH...

---

### Post by hraposo on 2006-09-16
I've two computers connected whit ubuntu and one make the connection with the   putty without problem. but the other no...

---

### Post by Endolith on 2008-01-31
I am having this problem too.  It seems to be related to DNS, since several people online say it can be fixed by setting "UseDNS" to "no".  Also, my connection is dropped after the password entry when I run it normally, but when I run PuTTY with -4 to force IPV4, it works (though slowly).

---

