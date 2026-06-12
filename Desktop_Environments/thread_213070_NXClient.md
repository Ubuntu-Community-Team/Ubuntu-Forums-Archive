---
title: "NXClient"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Dgurion on 2006-07-10
I recently setup the nomachine nxserver on my ubuntu system.. But whenever I try to log in from my windows machine it always timesout. Heres the details page from nxclient:

NX> 203 NXSSH running with pid: 2080
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 123.123.123.123 on port: 22
NX> 211 The authenticity of host '123.123.123.123 (123.123.123.123)' can't be established.
RSA key fingerprint is 12:a4:f3:a1:f6:6u:65:av:12:23:78:mn:1d:1a:1q:22.
Are you sure you want to continue connecting (yes/no)? 

I do say yes that I want to continue connecting but it just stays at "Connecting to 123.123.123.123" and then it gives me a timeout error.

---

### Post by WARnux on 2008-04-19
I'm having the same problem right now from Linux and Windows.
I can connect from my machine though.

In EVERY case
telnet domain port
connects to ssh perfectly.  Maybe it's a client version issue.  I'm upgrading the client on my other Linux machine to see if it helps.

---

### Post by WARnux on 2008-04-19
Didn't help at all.

---

### Post by WARnux on 2008-04-19
I'm almost positive it is my firewall.

---

### Post by WARnux on 2008-04-19
I've been trying all day and cannot connect.

I can connect from another machine using straight ssh but not with nx.

---

### Post by WARnux on 2008-04-20
Also, my firewall isn't the problem.  I took it down and still have the same issue.

---

### Post by WARnux on 2008-04-20
I beleive the problem lies in my router.
When I connect with an internet address, it doesn't work.
When I connect with a local 192.168 address, it works.

---

### Post by WARnux on 2008-04-20
Now I'm getting somewhere.
When using an IP (local or not) it works.  When using a domain name, it does not.

---

### Post by WARnux on 2008-04-21
I'm stumped.

It's not my firewall or my router because I took them both down and still have the same issue.

---

### Post by WARnux on 2008-04-21
I ran sshd in debug mode and it looks like it's a communication problem between ssh and nx.  I also tried to run nxssh but...

/usr/NX/bin/nxssh: error while loading shared libraries: libXcomp.so.3: cannot open shared object file: No such file or directory

Looks to me that you're not supposed to run it directly.  I tried forcing it by addin the lib dir in NX to the ld.so.conf but then I couldn't run things as root anymore with gksudo because apparently it needs sshd and won't work with nxssh.

---

### Post by WARnux on 2008-04-21
I should mention that it's possible this problem is exclusive to Ubuntu.  It always worked without a problem on Debian.

---

### Post by WARnux on 2008-04-23
Good news.  Still not sure why, but [www.domainName.com](www.domainName.com) works.  Without www it does not work.  That must be some kind of NX restriction.

---

