---
title: "How to enable command line remote login?"
date: 2008-02-28
forum: Desktop Environments
---

### Post by explainer on 2008-02-28
I am attempting to log in to another Linux system (a Gutsy Gibbon VM) using ssh.  

ssh test-web-server

and the reply is:

ssh: connect to host test-web-server port 22: Connection refused

So it seems that some daemon which should be waiting of port 22 is not enabled.  Caan anyone tell me what it should be and how I can enable it?:)

---

### Post by Whiffle on 2008-02-28
sudo apt-get install ssh


Its not installed by default, for some crazy reason.

---

### Post by PeterJS on 2008-02-28
There are two compoents to ssh, openssh-client and openssh-server. Openssh-client is installed by default and includes ssh which allows you to connect to other machines. Openssh-server includes sshd and is what allow remote machines to connect to you. You'll want to install openssh-server on the VM you're trying to connect to.

---

