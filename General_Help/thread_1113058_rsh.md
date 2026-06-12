---
title: "rsh"
date: 2009-04-01
forum: General Help
---

### Post by big136 on 2009-04-01
Hi,
on Linux RED HAT 
I issue :


 rsh ****.16.0.151 -l root ls -l /tmp 


and I receive :


connect to address ***.16.0.151: Connection refused
Trying krb4 rsh...


In hosts file of remote (***.16.0.151) I have :


***.16.0.202 root


Can you help me ?

Thank you.

Any way on my Linux machine I do not have .rhosts :

ls -al  *host*
[root@server oracle]# ls -al /etc/*host*
-rw-r--r--  1 root root  17 Jul 23  2000 /etc/host.conf
-rw-r--r--  2 root root 459 Apr  1 10:51 /etc/hosts
-rw-r--r--  1 root root 194 Sep  1  2006 /etc/hosts~
-rw-r--r--  1 root root 181 Dec 13  2007 /etc/hosts.allow
-rw-r--r--  1 root root 326 Oct 16  2007 /etc/hosts.bak
-rw-r--r--  1 root root   5 Nov  1  2004 /etc/hosts.canna
-rw-r--r--  1 root root 347 Jan 13  2000 /etc/hosts.deny
-rw-r--r--  1 root root 183 Sep  1  2006 /etc/hostssave
-rw-r--r--  1 root root 209 Aug 31  2006 /etc/hostssave~

---

### Post by mixmaster on 2009-04-01
I'm not sure what your problem is, although it is likely that the remote machine is not running rshd.

rsh is an inherently insecure protocol for general network usage.  You would do better to use ssh.

---

### Post by big136 on 2009-04-01
> **mixmaster said:**
> I'm not sure what your problem is, although it is likely that the remote machine is not running rshd.

rsh is an inherently insecure protocol for general network usage.  You would do better to use ssh.
Thank you.
I used this :

scp test.jsp root@remote:/tmp/
root@remote's password:



It works but how can I prevent asking password ?

Thank you.

---

### Post by mixmaster on 2009-04-01
You can set up ssh so that neither logon nor scp prompt for a password by adding a config file to your .ssh directory.  There is a beginners howto on creating the config file here : [http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

Remember however that if you do this, then anyone who can access your machine can also access the remote machine without any further security checks.  In general it is an extremely bad idea to automate root access.

---

### Post by big136 on 2009-04-06
> **mixmaster said:**
> You can set up ssh so that neither logon nor scp prompt for a password by adding a config file to your .ssh directory.  There is a beginners howto on creating the config file here : []()


Thank you but 
I can not see something about that here [http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

---

