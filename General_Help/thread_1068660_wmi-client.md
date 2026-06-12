---
title: "wmi-client"
date: 2009-02-13
forum: General Help
---

### Post by chandar on 2009-02-13
Hi all,
I installed 'wmi-client' provided by unbuntu.
But when i try to contact a remote server i get the following error.
Please help me on the same.

[B][root@test wmi-0.1.13]#./wmic -U username%paswds //x.x.X.X "select name from Win32_Service where State='Running'"
ERROR: dcom_create_object.
ERROR: Login to remote object.
NTSTATUS: NT_STATUS_IO_TIMEOUT - NT_STATUS_IO_TIMEOUT[/B]

Can Anyone help me on this... :(

With Regards
Chandar V Rao

---

### Post by BOK on 2009-02-19
Is WMI configured on the Windows-server?

Read this how to check:
[http://www.zenoss.com/community/docs/zenoss-guide/2.2.4/ch16s03.html](http://www.zenoss.com/community/docs/zenoss-guide/2.2.4/ch16s03.html)

---

### Post by QrK0 on 2009-04-20
Get exactly the same error message as reported in the first post.
WMI on the windows server is correctly setup according to:
> **BOK said:**
> Is WMI configured on the Windows-server?

Read this how to check:
[http://www.zenoss.com/community/docs/zenoss-guide/2.2.4/ch16s03.html](http://www.zenoss.com/community/docs/zenoss-guide/2.2.4/ch16s03.html)
It doesn't matter the query trying to issue, the error is always the same. On the Win server I see successfull logons in the security log.

Any clue on this will be appreciated

---

