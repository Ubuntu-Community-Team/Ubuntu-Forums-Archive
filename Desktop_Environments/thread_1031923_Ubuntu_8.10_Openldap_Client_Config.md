---
title: "Ubuntu 8.10 Openldap Client Config"
date: 2009-01-05
forum: Desktop Environments
---

### Post by joemanz on 2009-01-05
Hi everyone,

I'm having some issue with OpenLdap client on the Ubuntu 8.10. I've followed the LDAPClientAuthentication here [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) and I'm getting this error in the /var/log/auth.log

```

Jan  5 19:23:16 rtplxdt01 gdm[5042]: pam_unix(gdm:auth): check pass; user unknown
Jan  5 19:23:16 rtplxdt01 gdm[5042]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 

```

Here are the configurations for the PAM via auth-client-config:

```

[ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required        pam_env.so
        auth    sufficient      pam_unix.so likeauth nullok
        auth    required        pam_group.so use_first_pass
        auth    sufficient      pam_ldap.so use_first_pass
        auth    required        pam_deny.so
pam_account=account    sufficient   pam_unix.so
        account    sufficient   pam_ldap.so
        account    required     pam_deny.so
pam_password=password   required     pam_cracklib.so difok=2 minlen=8 dcredit=2 ocredit=2 retry=3
        password   sufficient   pam_unix.so nullok md5 shadow use_authtok
        password   sufficient   pam_ldap.so use_first_pass
        password   required     pam_deny.so
pam_session=session    required     pam_limits.so
        session required        pam_mkhomedir.so skel=/etc/skel/
        session    required     pam_unix.so
        session    optional     pam_ldap.so

```

I've also edit the /etc/security/group.conf to add assign local group to domain (LDAP) users:
```

*; *; *; Al0000-2400; users,adm,dialout,fax,cdrom,floppy,tape,audio,dip,video,plugdev,scanner,fuse

```

If anyone has come across this same issue, please let me know. Thanks in advance.


Joe

---

### Post by joemanz on 2009-01-06
Does anyone have this similar problem?

---

### Post by scix on 2009-01-22
I also have this problem, but only when using libpam-ccreds, installed using this guide: [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

I realy need to get this to work.

---

### Post by druhboruch on 2010-08-08
Anyone has a solution?

---

### Post by awe on 2010-08-09
This is the exact contents of my 'ldap' profile, which I use in conjunction with *auth-client-config*:
```
[open_ldap]
nss_passwd=passwd: compat ldap
nss_group=group: compat ldap
nss_shadow=shadow: compat ldap
nss_netgroup=netgroup: compat ldap
pam_auth=auth       required     pam_env.so
 auth       sufficient   pam_unix.so likeauth nullok
 auth       sufficient   pam_ldap.so use_first_pass
 auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
 account    sufficient   pam_ldap.so
 account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow use_authtok
 password   sufficient   pam_ldap.so use_first_pass
 password   required     pam_deny.so
pam_session=session    required     pam_limits.so
 session    required     pam_mkhomedir.so umask=0022 skel=/etc/skel/ silent
 session    required     pam_unix.so
 session    optional     pam_ldap.so
```
Please note that the line ```
session    required    pam_mkhomedir.so umask=0022 skel=/etc/skel/ silent
``` needs all these arguments since 8.10 in order to create user the user home directory and all its skeleton correctly upon first login. The *silent* is not mandatory, it just saves you from clicking on "OK" on a promt window or two upon first login, but it's good to put it in because sometimes the end-user knows little about computers and freaks out when presented with the prompts.

I wonder if the profile will work well with you. Works well with me, I can't count how many times I've setup this and all has always gone well.

---

