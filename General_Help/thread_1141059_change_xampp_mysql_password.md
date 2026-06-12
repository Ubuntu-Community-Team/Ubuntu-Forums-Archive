---
title: "change xampp mysql password"
date: 2009-04-28
forum: General Help
---

### Post by dem3nte on 2009-04-28
hi im using mysql through xampp and i want to change the password that i currently have for mysql. Ive tried looking and can find alot of information on how to change it on windows and other scenarios but what ive tried upto now hasnt been succesfull. can anyone help me ?

---

### Post by Titan8990 on 2009-04-28
The password for a user stored in the database? The password of the mysql root user? The password of a mysql user (with permissions to a database)?


User is overly vague as it could be any of the three above (all with different ways of changing). 


mysql commands are OS independent. A mysql shell is the same on linux, windows, solaris, bsd, etc.

---

### Post by dem3nte on 2009-04-28
i mean the password to actually enter mysql eg. /opt/lam.../mysql -u root -p
how to change the password im prompted for

---

### Post by Titan8990 on 2009-04-28
sudo dpkg-reconfigre mysql-server


You can thank debian developers for making it that easy later.

---

### Post by dem3nte on 2009-04-28
i tried that earlier but got mysql-server is not installed etc... i assume because i have it installed as a part of xampp and didnt install it individually ?

---

### Post by Titan8990 on 2009-04-28
Yes, get rid of xampp and install the stack the correct way: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

