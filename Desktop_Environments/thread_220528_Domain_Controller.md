---
title: "Domain Controller"
date: 2006-07-21
forum: Desktop Environments
---

### Post by sparty2809 on 2006-07-21
I followed the following [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10).  I used Ubuntu 6.06 Server.  I can log into the domain fine.  However, once I put my machine behind the firwall, I can't.  It says something about a DNS problem.  Any ideas how to fix this?  I need this to work for Linux and Windows (some staff are on Windows still :rolleyes:).

Here is the windows error:
Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\WINDOWS\debug\dcdiag.txt.

The following error occurred when DNS was queried for the service location (SRV) resource record used to locate a domain controller for domain domain:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.domain

Common causes of this error include the following:

- The DNS SRV record is not registered in DNS.

- One or more of the following zones do not include delegation to its child zone:

domain
domain
com
. (the root zone)

For information about correcting this problem, click Help.

---

