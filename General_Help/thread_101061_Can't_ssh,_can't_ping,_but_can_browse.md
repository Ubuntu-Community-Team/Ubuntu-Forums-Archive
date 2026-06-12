---
title: "Can't ssh, can't ping, but can browse?"
date: 2005-12-09
forum: General Help
---

### Post by trytrytry on 2005-12-09
(I searched the forum and didn't find the similar one. I am sorry if I missed)

Hi All,

I installed the Ubunut 5.10 on my school's computer. Everything seems working fine except the ssh. I installed the ssh and openssh-server and I can see them running behind, but I can't ssh the machine from my laptop (running winxp).  As suggested by  someone  in  my other post, I tried this on my Ubuntu machine:

telnet 127.0.0.1 22
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4
....
(suspended here, after I typed space, then)
....
Protocol mismatch.
Connection closed by foreign host.


I can browse yahoo and google without any problem but I can't ping them. Once I ping yahoo, I got
"PING [www.yahoo.akadns.net](www.yahoo.akadns.net) (68.142.197.70) 56(84) bytes of data."
(then no response)
It is the same when I log out and enter my computer through my winxp pro.

But I can ping the computers in my local network and vice verva.

I can use "ssh [email]myusername@abc.def.edu[/email]" to successfully connect to outside computers where  I have account. But they can't ping or ssh back to my ubuntu machine.

I checked my hosts.allow and hosts.deny and both are empty. Is it normal? Should I make any configuration changes?

Can anyone give me some suggestions?

This is quite an urgent problem for me since SSH is one of the main reasons I installed linux on the machine. Many thanks in advance.

---

### Post by nystire on 2005-12-09
The part where you say that you can't ping the outside network but you can ping local machines sounds like a firewall in action. Try speaking to your network administrator about it. They may have decided to block off everything but port 80 (http) and 443(https) which could account for your being able to browse but not do anything else.

---

### Post by Lofticus on 2005-12-09
Can you ssh anything else? 

Maybe a check for port 22 (thats normally the ssh port) would help?

---

