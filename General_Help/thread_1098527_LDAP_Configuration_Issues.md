---
title: "LDAP Configuration Issues"
date: 2009-03-17
forum: General Help
---

### Post by sswittch on 2009-03-17
Hi,

I have been following a readme on how to install a postfix virtual hosting with ldap backend and with dovecot pop3 imap on ubuntu8.10.

Every seem to be going ok, however I have now run into a brick wall.

[http://howtoforge.org/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10](http://howtoforge.org/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10)

I am up to acl-del.ldif

acl-del.ldif
```
dn: olcDatabase={1}hdb,cn=config
delete: olcAccess 
olcAccess: to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=example,dc=tld" write by anonymous auth by self write by * none 
olcAccess: to dn.base="" by * read 
olcAccess: to * by dn="cn=admin,dc=example,dc=tld" write by * read
```

After Excecuting
```
root@ritzphoto:/usr/src/phamm-inst# ldapmodify -x -D cn=admin,cn=config -W -f acl-del.ldif
Enter LDAP Password: 
ldapmodify: wrong attributeType at line 3, entry "olcDatabase={1}hdb,cn=config"

```

/etc/ldap/slapd.d/cn\=config/olcDatabase\=\{1\}hdb.ldif
```
dn: olcDatabase={1}hdb
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=example,dc=tld
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=example,dc=tld" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=example,dc=tld" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
structuralObjectClass: olcHdbConfig
entryUUID: 28266130-a719-102d-87dc-5db797f6f852
creatorsName: cn=admin,cn=config
createTimestamp: 20090317082711Z
entryCSN: 20090317082711.660412Z#000000#000#000000
modifiersName: cn=admin,cn=config
modifyTimestamp: 20090317082711Z


```

Any help would be greatly appreciated

---

