---
title: "Problems with update manager"
date: 2009-04-09
forum: General Help
---

### Post by jcorden on 2009-04-09
Trying to update my installation and getting the following error message from update manager

'E:Malformed line 40 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Any ideas?

---

### Post by taurus on 2009-04-09
There is something wrong with line 40 in your /etc/apt/sources.list.  Therefore, you need to edit it to correct that problem.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
If not sure, post the whole thing here.

---

