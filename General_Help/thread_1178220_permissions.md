---
title: "permissions"
date: 2009-06-04
forum: General Help
---

### Post by baraber on 2009-06-04
i have to change some files in googleearth properties,but i dont have permission,say that root is the owner,how to fix that,to became the owner?
thanx:KS

---

### Post by maflynn on 2009-06-04
I would think if you want to change the owner, you'd use chown with the appropriate flags.  Just do a man chown to see the flags.

---

### Post by Soul-Sing on 2009-06-04
You can use: ```
gksudo nautilus
```
Do your "google"job, and please close nautilus.

---

### Post by baraber on 2009-06-04
more specific,please,i am new in this,i tried in terminal,but i am not shure that i doing that right

---

### Post by CapnBoost on 2009-06-04
you can either right click on the file > properties > permissions

or you can use [chmod and character or number codes]("https://help.ubuntu.com/community/FilePermissions").

---

### Post by baraber on 2009-06-04
thanx leoquant,that worked:popcorn:

---

