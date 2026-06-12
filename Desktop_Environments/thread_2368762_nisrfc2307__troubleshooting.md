---
title: "nis/rfc2307  troubleshooting"
date: 2017-08-14
forum: Desktop Environments
---

### Post by jeff.sadowski on 2017-08-14
So I had created a new machine and joined it via samba using rfc2307
I have used this with many machines with no issues.
On the newly installed machine I was having issues with a subset of users not being able to login.

First thing in troubleshooting check each item in yppasswd or on the "UNIX Attributes" tab
Make sure they have a uniq uid, that their home directory exists that they are assigned to an NIS Domain(Windows only), make sure they are assigned to a Primary group that has a gid, make sure their login shell exists.

Turns out my users shell didn't exist.
Nothing in the logs suggested looking into that.

/var/log/auth.log was showing this
```

Aug 14 14:44:40 logan sshd[1447]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 14 14:44:40 logan sshd[1447]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 14 14:44:40 logan sshd[1447]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_LOGON_FAILURE, Error message was: Logon failure
Aug 14 14:44:40 logan sshd[1447]: pam_winbind(sshd:auth): user 'myusername' denied access (incorrect password or invalid membership)
Aug 14 14:44:42 logan sshd[1447]: Failed password for invalid user myusername from 192.168.0252 port 40632 ssh2

```

---

### Post by TheFu on 2017-08-15
Just posting this here, so that others know that NIS (also called yp) has a number of poor security issues that cannot be fixed. [https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Security_Guide/s1-server-nis.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Security_Guide/s1-server-nis.html)  It can be run in an air-gapped network where all clients and servers can be trusted.  NIS is really a set of protocols that should have died with telnet, rlogin, rcp, and plain FTP.  

The MSFT Kerberos implementation was hacked a few years ago and wasn't patched for at least 2 years, if ever.  IDK.  [http://resources.infosecinstitute.com/windows-kerberos-vulnerability-need-know/](http://resources.infosecinstitute.com/windows-kerberos-vulnerability-need-know/) 

NIS+ or a non-MSFT LDAP implementation with Kerberos should be used instead.  NIS+ server only runs on Oracle Solaris, sadly. F/LOSS NIS+ clients exist for Linux, Unix, OSX, and Windows.

---

