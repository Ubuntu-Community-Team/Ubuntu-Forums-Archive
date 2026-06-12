---
title: "ODBC, mysql and openoffice"
date: 2006-11-02
forum: Desktop Environments
---

### Post by biodiesel-bri on 2006-11-02
I am using OpenOffice base to connect to a MySQL database through ODBC.  OpenOffice opens and reads the mysql database. I can do queries that don't use the sum or count function and they work.

But... whenever I try to do a query that uses sum or count, OpenOffice locks up.  I can do a sum through isql. 

Has anybody gotten this to work?  I used to be able to do this (about a year ago), but no more.

---

### Post by marianom on 2006-11-02
See if this bug report is the same as your problem:
[http://www.openoffice.org/issues/show_bug.cgi?id=60273](http://www.openoffice.org/issues/show_bug.cgi?id=60273)

It mentions there certain situation where it cannot be fixed (!!).

---

### Post by biodiesel-bri on 2006-11-24
No, that looks like a different bug.  This is the one I submitted:
[http://www.openoffice.org/issues/show_bug.cgi?id=64976](http://www.openoffice.org/issues/show_bug.cgi?id=64976)

They closed it, claiming it was a (k)ubuntu bug.  I can get it to work with 2.0.1 and Breezy.

---

