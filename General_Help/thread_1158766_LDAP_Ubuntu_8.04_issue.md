---
title: "LDAP Ubuntu 8.04 issue"
date: 2009-05-14
forum: General Help
---

### Post by vasquezj on 2009-05-14
Hello, 
 
I need some help in defining the LDAP baseDN to search all OUs in active directory 2003 R2. My AD layout is as follows:
 
test.com
   OU_1-- some users  
   OU_2-- other users
   ...
   users -- other users
 
I need to ensure that the baseDN is capable of searching all containers (OUs and default users container).
 
The current baseDN defined only allow me to search the users container
cn=users,dc=test,dc=com
 
The rootDN is defined as follows:
cn=administrator,cn=users,dc=test,dc=com
 
Any help is appreciated
 
Thanks ....

---

