---
title: "Samba Xinetd and install errors"
date: 2006-08-26
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-26
I installed xinetd for VMware Server to use. Am I really a Xinetd user if I only have it for one program? Also, why am I getting so many errors, and what should I do. This never happened before? I'm going to use samba with my xp virtual machine.

```
veronica@veronica-desktop:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 7250kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 103985 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
Setting up samba (3.0.22-1ubuntu3.1) ...
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons...                                             [ ok ]

veronica@veronica-desktop:~$
```

---

### Post by maybeway36 on 2007-08-27
I have xinetd for x11vnc, but Samba still seems to work for me without adding an xinetd entry. Why is the warning there, then?

---

