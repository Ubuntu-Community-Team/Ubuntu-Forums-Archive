---
title: "ssh not working on fresh install of Ubuntu server 8.04"
date: 2009-06-03
forum: General Help
---

### Post by mrotsliah on 2009-06-03
I'm practicing setting a server for the first time.  I try to ssh into the server from a number of other machines, but the connection is always closed by the server.  It looks like it is trying to use port 22.  In /etc/hosts.allow, it is all commented out.  I tried adding 
ALL : ALL
just to see if I could get anything, but it didn't work.

---

### Post by blueridgedog on 2009-06-03
Can you ssh to yourself on the server?

```
ssh 127.0.0.1
```

Also, is /etc/hosts.deny empty?

---

### Post by jonobr on 2009-06-03
Hello

Just wondering if you have installed open SSH from your synptic package manager

---

### Post by Iowan on 2009-06-03
**openssh-client** should already be installed, but **openssh-server** may not be.

---

