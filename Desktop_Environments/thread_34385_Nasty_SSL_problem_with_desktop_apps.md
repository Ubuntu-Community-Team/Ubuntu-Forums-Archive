---
title: "Nasty SSL problem with desktop apps"
date: 2005-05-14
forum: Desktop Environments
---

### Post by brockmeister on 2005-05-14
My Hoary setup is giving my some rather sticky problems with various network protocols.

Firefox isn't opening pages which use the https protocol - it stays on the 'Connecting to blah.blah.net' stage forever. It also does this with ftp, and in fact any protocol except plain http.

I'm getting some similar problems with the command-line sftp, as well as Nautilus when dealing with ftp and sftp. Synaptic is also not working with ftp, and I can't access my old POP3/SMTP email account.

The really strange thing is that all of these work if I type in an IP address (instead of a domain name). This kind-of solves the problem for some things, but, for instance, I can't get at my Gmail because if I type in any one of the many Gmail IP addresses (like  66.102.9.105) it just gives me the normal Google homepage.

I have a fully updated version of Hoary/x86. I've also tried reinstalling Firefox, OpenSSL, libssl and OpenSSH, to no avail.

Sorry that I couldn't file a bug report - of course the Ubuntu bugzilla uses SSL so I can't get at it.

---

