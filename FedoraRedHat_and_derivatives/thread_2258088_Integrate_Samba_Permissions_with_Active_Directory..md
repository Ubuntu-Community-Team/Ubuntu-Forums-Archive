---
title: "Integrate Samba Permissions with Active Directory."
date: 2014-12-24
forum: Fedora/RedHat and derivatives
---

### Post by hack3rcon on 2014-12-24
Hello Folks.How are you?I joined my CentOS into Windows Domain and I want to give Permission to files and Directory via Active Directory. When I use "getent passwd" and "getent group", I can see All AD users and Groups. I use below command to give Permission to a Folder via ACL :```
setfacl -m g:"jasondomain\jason-rw":rwx /home/local/jasondomain/jason/test
```and I create a part for my "smb.conf" file :```
[Test][comment = testpath = /home/local/jasondomain/jason/testbrowsable = yesinherit acls = yesinherit permissions = yesinherit owner = yesmap acl inherit = yesacl check permissions = yesnt acl support = yes#valid users = %D\%S#write list = @jasondomain\domain^adminsread only = no
```but when I browse the "Test" directory it ask me username and password and when I enter "jasondomain\jason" as username it can't let me to open the "Test" directory. What is the problem?Cheers.

---

