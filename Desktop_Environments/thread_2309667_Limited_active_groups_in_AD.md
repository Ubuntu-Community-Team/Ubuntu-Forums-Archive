---
title: "Limited active groups in AD"
date: 2016-01-12
forum: Desktop Environments
---

### Post by jeff.sadowski on 2016-01-12
I am using ubuntu 14.04
samba 4.1.6

My /etc/samba/smb.conf looks as follows
```
[global]
   security = ads
   realm = SUBDOMAIN.DOMAIN
   workgroup = SUBDOMAIN
   idmap config * : backend = tdb
   idmap config * : range = 2000-7999
   idmap config SUBDOMAIN:backend = ad
   idmap config SUBDOMAIN:schema_mode = rfc2307
   idmap config SUBDOMAIN:range = 8000-9999999
   idmap uid = 8000-99999
   idmap gid = 8000-99999   
   winbind nss info = rfc2307
   winbind use default domain = yes
   winbind nested groups=yes
   winbind expand groups=10
   winbind enum users = yes
   winbind enum groups = yes
   restrict anonymous = 2

```

I joined the domain as follows
```

net ads join -UAdministrator

```

I can list all the users with
```
wbinfo -u
```
I can list all the groups with
```
wbinfo -g
```
I can list all the menbers of the group with
```
getent group sudoers
```
and if I do
```
id $USER
```
sudoers is listed
but if I only do
```
id
```
it is not listed.
I can use
```
newgrp sudoers
```
to change my group and then do what I need but I am puzzled as to why some of the groups show with id and some do not unless I run it with the users name
```
id -G|sed 's/ /\n/g'|wc -l
```
shows
```
29
```
```
id $USER -G|sed 's/ /\n/g'|wc -l
```
shows
```
154
```
if I remove non valid groups
```
id -G|sed 's/ /\n/g'|grep -v 4294967295|wc -l
```
shows
```
29
```
```
id $USER -G|sed 's/ /\n/g'|grep -v 4294967295|wc -l
```
shows
```
143
```

---

