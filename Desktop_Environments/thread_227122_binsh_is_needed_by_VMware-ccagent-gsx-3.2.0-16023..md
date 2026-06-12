---
title: "/bin/sh is needed by VMware-ccagent-gsx-3.2.0-16023.i386"
date: 2006-08-01
forum: Desktop Environments
---

### Post by berginj on 2006-08-01
Ok I have done some searching on what this issue is.
#1 in order to get this agent even this far I had to install RPM
#2 the program is executed as follows:
/# sh ccagent
error: Failed dependencies:
        /bin/sh is needed by VMware-ccagent-gsx-3.2.0-16023.i386
#3 I went and read a number of postings and did the following
3.a - removed and reinstalled bash
3.b installd dash and zash
3.c deleted the sh link to bash and recreated
"ln -s bash sh"

Help! Thanks

---

