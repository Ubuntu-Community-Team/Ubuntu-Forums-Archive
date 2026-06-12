---
title: "ftp server"
date: 2009-04-13
forum: General Help
---

### Post by hive225 on 2009-04-13
So I've been trying to find a good ftp server to put on one of my boxes (must allow fxp). So far I've tried Pure-ftpd, Proftpd, and Crossftp. I couldn't get any of them to fxp anything, and crossftp wouldn't even load.

I'm running 8.04

Can anyone offer some help? Or suggest the best ftp server?

---

### Post by hw-tph on 2009-04-13
Sounds like you haven't gotten your configurations correct. Or perhaps the server sits on a private IP using NAT being accessible from the Internet? Anyhow, vsftpd works for me and it is very easy to configure.

---

