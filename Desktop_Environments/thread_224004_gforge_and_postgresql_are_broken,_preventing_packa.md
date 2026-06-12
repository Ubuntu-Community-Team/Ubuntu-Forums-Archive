---
title: "gforge and postgresql are broken, preventing packages from installing"
date: 2006-07-27
forum: Desktop Environments
---

### Post by shiidii on 2006-07-27
Hey, I started learning Ubuntu a month ago and all is going swimmingly, until now. I'm using an Ubuntu Dapper Drake server.
I'm not sure which of the two packages aren't working right, but something's wrong and it's having a bad impact on anything being installed.

Here's the long list of errors. That appears when I try installing anything mail-related.

```
Configuring for PostgreSQL 7.3 or later
create OKCannot enable the PLPGSQL language in the database...  This shouldn't have happened.
Maybe a problem in your PostgreSQL configuration?
Please report a bug to the Debian bug tracking system
Please include the following output:
enable_lang's STDOUT:
enable_lang's STDERR:
sh: /usr/lib/postgresql/bin/enable_lang: No such file or directory
dpkg: error processing gforge-db-postgresql (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gforge-ldap-openldap:
 gforge-ldap-openldap depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-ldap-openldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-cvs:
 gforge-cvs depends on gforge-ldap-openldap | gforge-ldap; however:
  Package gforge-ldap-openldap is not configured yet.
  Package gforge-ldap is not installed.
  Package gforge-ldap-openldap which provides gforge-ldap is not configured yet.
dpkg: error processing gforge-cvs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-dns-bind9:
 gforge-dns-bind9 depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-dns-bind9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-ftp-proftpd:
 gforge-ftp-proftpd depends on gforge-ldap-openldap | gforge-ldap; however:
  Package gforge-ldap-openldap is not configured yet.
  Package gforge-ldap is not installed.
  Package gforge-ldap-openldap which provides gforge-ldap is not configured yet.
dpkg: error processing gforge-ftp-proftpd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-shell-ldap:
 gforge-shell-ldap depends on gforge-ldap-openldap | gforge-ldap; however:
  Package gforge-ldap-openldap is not configured yet.
  Package gforge-ldap is not installed.
  Package gforge-ldap-openldap which provides gforge-ldap is not configured yet.
dpkg: error processing gforge-shell-ldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-web-apache:
 gforge-web-apache depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-web-apache (--configure):
 dependency problems - leaving unconfigured
Setting up isoqlog (2.2-0.3) ...
/var/lib/dpkg/info/isoqlog.postinst: line 61: [: too many arguments
/var/lib/dpkg/info/isoqlog.postinst: line 64: [: too many arguments
cp: cannot copy a directory, `\342', into itself, `\342/\342'
cp: cannot copy a directory, `\342', into itself, `\342/\342'
cp: cannot copy a directory, `\342', into itself, `\342/\342'
dpkg: error processing isoqlog (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql
 gforge-ldap-openldap
 gforge-cvs
 gforge-dns-bind9
 gforge-ftp-proftpd
 gforge-shell-ldap
 gforge-web-apache
 isoqlog

```

I'm guessing that I will need to remove gforge and posgresql and reinstall, but I'm not sure how much of an impact it will have on the server and if there is any critical data loss. Any help I would extremely appreciate to no end.

---

### Post by rshel on 2006-09-12
I'm having the same problem. Can't install postgresql 8.1 without uninstalling gforge and 7.4.  Did you ever figure it out or get an answer?

---

### Post by kahuuna on 2006-09-30
omg gah just installed gforge-ftp-proftpd and now having dependency issues! god I hate this...

---

### Post by yusufk on 2007-04-26
Still broken in feisty.

:confused:

---

