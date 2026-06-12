---
title: "Remote Desktop works for one user but not another"
date: 2016-05-06
forum: Desktop Environments
---

### Post by david518 on 2016-05-06
New Ubuntu 14.4 desktop installation.

Installed XRDP
Installed Mate Desktop 1.8.2
modified /etc/xrdp/startwm.sh to create .xsession for each user.
added second user
added second user to all groups the primary user was in.

The primary user (created when I installed Ubuntu) works fine locally, or via Remote Desktop from windows.

The second user works locally, but gets a solid gray screen when I try to access via Remote Desktop.

I have also tried this with the LXDE desktop, and got the same results.

.xsession contains:

```
Xsession: X session started for  at Fri May  6 10:38:52 CDT 2016
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:xxx being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
/etc/xrdp/startwm.sh: 8: [: x: unexpected operator
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
/etc/xrdp/startwm.sh: 3: [: x: unexpected operator
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
/usr/bin/im-launch: 35: exec: /bin/bash
: not found
Xsession: X session started for  at Fri May  6 11:00:09 CDT 2016
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:xxx being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
/etc/xrdp/startwm.sh: 8: [: x: unexpected operator
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
/etc/xrdp/startwm.sh: 3: [: x: unexpected operator
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
/usr/bin/im-launch: 35: exec: /bin/bash
: not found
```

-----------

---

### Post by david518 on 2016-05-09
What other log file should I be looking at to try to debug this, or are there other steps to take to gather more information?

---

### Post by david518 on 2016-05-10
I don't know why this caused the problem, but it caused all kinds of other problems.

When I created the other user accounts, I used the newusers command.  It added a ^M at the end of each line in passwd.  Removed that and Remote Desktop is working.

---

