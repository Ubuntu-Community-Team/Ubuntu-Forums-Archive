---
title: "documentations."
date: 2009-04-09
forum: General Help
---

### Post by StOoZ on 2009-04-09
I installed using the synaptic several doc packages :
mysql-doc-5.0 ,  sqlite-doc , sqlite3-doc

how do I read them??? 
I cant find them when searching with 'man -k sql'

---

### Post by Wayne_V on 2009-04-09
To see what is installed with a package do:

$ dpkg --listfiles <packagename>

---

### Post by Claus7 on 2009-04-09
Hello,

also this will help you:
```
cd /
find -name "**name_you_wish**"
```

in *name_you_wish* put the name of the doc you want to find. You 'd better not remove the * and the "" when you type the above command.

In order to read them type less and the path in which belongs the file you are looking for.

Regards!

---

### Post by cariboo on 2009-04-09
Most documentation is stored in /usr/share/doc. To open the directory go to Places-->Home Folder-->Files System-->usr-->share-->doc.

Jim

---

