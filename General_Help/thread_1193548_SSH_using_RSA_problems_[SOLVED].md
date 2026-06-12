---
title: "SSH using RSA problems [SOLVED]"
date: 2009-06-21
forum: General Help
---

### Post by ScottMartin on 2009-06-21
Trying to setup a SSH to a local ubuntu server and I was unable to get it to work as expected.

Client error messages: Permission denied (public key)
Server log (sshd: Received signal 15; terminating) 

I found the following article and setup SSH as described:
[http://blog.agdunn.net/?p=54]("http://blog.agdunn.net/?p=54")

This is all on a lan for now, but it will become a remote setup soon.

-sshd_config file has been properly updated, rechecked.. again.
-Authorized_Keys file ~/.ssh (dir at 700, files at 600)
-I can telnet locally and from client PC
-Firewall setup correctly, can ping/telnet server as mentioned
-I can connect using password enabled, just not RSA method
-Removed known_hosts, jic
-Ate lunch

ssh -vvv was showing failure, but no obvious reason.

I have also deleted the authorized_keys on the server and used the method:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@server
```
to recreate the key.

In spending several hours on this, I was able to solve the problem as follows:

I had placed the authorized_key file in the ~/.ssh of the username on the server. I decided to set LogLevel DEBUG3 in sshd_config and try again.

SSH was trying to load the keys from /root/.ssh and not ~/.ssh

Copied the the files over, updated the rights .. poof! All working.

I learned a lot today, that makes it a good day!

Regards,
Scott.

---

