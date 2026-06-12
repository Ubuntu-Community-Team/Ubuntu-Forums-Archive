---
title: "Access denied error"
date: 2022-01-13
forum: Desktop Environments
---

### Post by shekapls on 2022-01-13
We are using ubuntu 18.04, join domain with AD 2008 r2 server. After restart, not able to log in with domain user ID
getting access denied error. We are frequently getting any bday has a fix for this please share to fix this

---

### Post by TheFu on 2022-01-13
[https://docs.microsoft.com/en-us/troubleshoot/windows-server/windows-server-eos-faq/end-of-support-windows-server-2008-2008r2](https://docs.microsoft.com/en-us/troubleshoot/windows-server/windows-server-eos-faq/end-of-support-windows-server-2008-2008r2)
says that Server 2008 R2 supported ended 2 yrs ago.
Well past time to move to a newer release.  

You can use Ubuntu as a Domain Controller, [https://ubuntu.com/server/docs/samba-domain-controller](https://ubuntu.com/server/docs/samba-domain-controller) according to that link.

---

### Post by ActionParsnip on 2022-01-14
You can add Ubuntu systems to AD but 2008 is long dead.

---

