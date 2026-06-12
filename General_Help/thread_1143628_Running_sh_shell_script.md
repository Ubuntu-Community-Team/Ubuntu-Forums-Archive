---
title: "Running sh shell script"
date: 2009-04-30
forum: General Help
---

### Post by chamnap on 2009-04-30
I have trouble with sh command since I am a newbie user. I want to write a shell script which need to run serveral mysql commands. Everything is going well except those command that need to run in mysql like source test.sql, use test_db. Could anyone show me how to code this? Really appreciate your help.

Thanks
chamnap

---

### Post by geirha on 2009-04-30
Sending the commands to stdin of mysql should work. E.g.:
```

mysql -u username << EOF
source test.sql;
use test_db;
EOF

```

---

### Post by chamnap on 2009-04-30
Great. Do you have any links that I can learn to master linux command or shell script? Thanks.

---

### Post by geirha on 2009-05-01
The two bash guides at [http://tldp.org/guides.html](http://tldp.org/guides.html) are quite good; Bash Guide for Beginners and Advanced Bash-Scripting Guide.

---

### Post by chamnap on 2009-05-01
Thanks alot.:)

---

