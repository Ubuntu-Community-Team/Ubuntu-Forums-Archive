---
title: "openldap unable to change passwords"
date: 2009-01-26
forum: General Help
---

### Post by Vezoo on 2009-01-26
Hi folks,

I set this up about two years ago but for the life of me I can't figure out what I am doing wrong.

I did follow the LDAP client authentication howto on the Ubuntu Community site but I know I am missing something.

I've got LDAP authentication working fine for all users however the users are unable to change their passwords via the 'passwd' command.  I get the following error when I use the "passwd" command.


```


user@server01:~$ passwd
Enter login(LDAP) password: 
New password: 
Re-enter new password: 
LDAP password information update failed: Server is unwilling to perform
shadow context; no update referral
passwd: Permission denied
passwd: password unchanged
user@server01:~$


```

I've pasted the bits of the configuration files I've modified.

```

usern@server01:/etc/pam.d$ grep ldap *
common-account:account sufficient	pam_ldap.so
common-auth:auth	sufficient	pam_ldap.so
common-password:password   sufficient pam_ldap.so
common-session:session sufficient      pam_ldap.so
user@server01:/etc/pam.d$


```

/etc/pam_ldap.conf

```

host 192.168.0.1

base dc=int,dc=server,dc=net,dc=au
uri ldap://192.168.0.1/, ldap://192.168.0.2
ldap_version 3
rootbinddn cn=admin,dc=int,dc=server,dc=net,dc=au
pam_password crypt

```

/etc/nsswitch/conf

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by Vezoo on 2009-01-27
Still no love?

---

