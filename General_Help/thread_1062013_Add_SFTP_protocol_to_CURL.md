---
title: "Add SFTP protocol to CURL ?"
date: 2009-02-06
forum: General Help
---

### Post by mkulon on 2009-02-06
I need to use SFTP from a script, and I was hoping to use CURL.  I know this is possible.  However, when I type:

**curl -V**

I get the following:
[B]curl 7.18.2 (x86_64-pc-linux-gnu) libcurl/7.18.2 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.8
Protocols: tftp ftp telnet dict ldap ldaps http file https ftps
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz
[/B]

The SFTP protocol is missing.  How do I add the sftp protocol to CURL?

---

### Post by nepoc on 2009-07-10
I have the same problem.

Anyone out there have answers?

I really don't feel like making a new custom deb.


Cheers

---

### Post by boscorama on 2010-08-06
Hi,

It's been a year now since this was posted.
Has anyone got a resolution to this?

I just ran up against it as an issue in Lucid (server). :(

TIA,
Bosco.

---

### Post by muriwo on 2010-08-28
Hi, a bug has been open for a while on this, I just found it.   The workaround detailed on post #3 (for 9.04) worked for me on 10.04 so I posted a tweaked set of instructions in post #10.  Odds are it would work for 9.10 as well.
[https://bugs.launchpad.net/ubuntu/+source/curl/+bug/311029](https://bugs.launchpad.net/ubuntu/+source/curl/+bug/311029)

---

