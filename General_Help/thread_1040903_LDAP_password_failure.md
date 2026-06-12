---
title: "LDAP password failure?"
date: 2009-01-16
forum: General Help
---

### Post by ryanfx on 2009-01-16
Hey everyone... I have a problem on 8.10 that's driving me insane

```

 sudo apt-get install slapd
sudo: cannot get working directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1467kB of archives.
After this operation, 3965kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 137458 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.11-0ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Setting up slapd (2.4.11-0ubuntu6) ...
  Moving old database directory to /var/backups:
  - directory unknown... done.
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... done.
Reloading AppArmor profiles : done.
Starting OpenLDAP: slapd.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

during this install it prompts me for a password... then I try to run the slapadd command and receive the error:

```
hdb_db_open: database "dc=elegant,dc=local": database already in use.
backend_startup_one: bi_db_open failed! (-1)
slap_startup failed
```

I am trying to follow some guides on setting up a primary domain controller and can't get past the first couple steps because of this..

I have also run: /etc/init.d/slapd start to make sure the server was started and no error messages were outputted to the console..


my syslog is showing:

```
Jan 16 01:35:12 esiserver kernel: [20164.104942] slapd[20296]: segfault at 4 ip b7f0c8fa sp b6de68a0 error 4 in slapd[b7eed000+127000]
```

---

