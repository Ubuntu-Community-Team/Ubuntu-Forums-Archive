---
title: "jdbc mysql problem"
date: 2009-04-13
forum: General Help
---

### Post by cheriansabs on 2009-04-13
hi Everybody,

I am facing this peculiar problem related to mysql.
When I write a stand alone java file to to access the mysql server writing the standard jdbc mysql connection code 
I have no problems at all.

But when I try to connect to a mysql server through a server side class using the same standard jdbc mysql connection code I get the following exception.
Caused by: java.security.AccessControlException: access denied (java.lang.RuntimePermission modifyThreadGroup)

Could anyone enlighten me as to why this would occur.

I am using Eclipse IDE and GWT(Google Web toolkit) code.


regards,
Cherian

---

### Post by cheriansabs on 2009-04-13
I'm sure this is not a code related issue. As the same works flawlessly in windows. It has something to do with the security of Ubuntu.
Any pointers..

---

