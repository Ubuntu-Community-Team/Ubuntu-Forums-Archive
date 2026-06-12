---
title: "passwordless ssh"
date: 2006-02-11
forum: Desktop Environments
---

### Post by 12quality on 2006-02-11
I recently got passwordless ssh working by generating a public key (with a passphrase) and adding it to ssh-agent.  It works fine with a server I own (also running Ubuntu), but it will not work on machines at my university (they are CentOS).  The only real difference I can see is that my username on my two machines is "seth", while my username on the university machines is "sds8".  

I normally log in using "ssh -l sds8 server.host.name" and then type my password, which is fine, but I was hoping to do it without passwords.  If I try that now, it still prompts me for a password.  If I type "ssh -l sds8 -o PreferredAuthentications=publickey server.host.name", it replies "Permission denied (publickey,gssapi-with-mic,password)".

It clearly supports public key authentication, and I checked that the permissions were set the exact same on both my server and the university server.

Help, please.

---

### Post by art on 2006-02-12
Well, as far as I understand you still need a password if you use key with a passphrase if you haven't configured ssh-agent. You can read all details with a very good howto here
[http://www-128.ibm.com/developerworks/library/l-keyc.html](http://www-128.ibm.com/developerworks/library/l-keyc.html)
. Or you can do the same with key without passphrase, if the computers you log on from are physically secure, because the data transmission in ssh is encrpyted. Anyway I hope following the howto you will get it working, I did at some point.

---

### Post by 12quality on 2006-02-12
I figured out the problem.  The university machines store user data on an afs share.  AFS isn't mounted until after login, so the ssh key can't be accessed.  Looks like the problem won't be solved.  If any inginuitive person can think of a way to get passwordless logins, please share.  I do think the servers support kerboros.

---

