---
title: "FTP server"
date: 2009-10-29
forum: Desktop Environments
---

### Post by paul99 on 2009-10-29
Hi,

Running 9.04. Tried setting up an FTP server using vsftp and proftp.  In both cases, I can telnet to the FTP server on port 21 from a remote box.

I can ftp the server, but after I enter the username and password, I get:

$ ftp 142.174.84.82
Connected to 142.174.84.82.
220 FTP server ready
User (142.174.83.80: (none)): ftpuser
331 User name okay, need password for ftpuser
Password:
530 Access denied
Connection closed by remote host.

Any ideas what's missing.  I'm running in stand-alone mode.

Thanks,

Paul

---

