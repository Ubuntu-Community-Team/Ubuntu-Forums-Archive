---
title: "Startup errors"
date: 2006-07-16
forum: Desktop Environments
---

### Post by electroconvulsive on 2006-07-16
z

---

### Post by philippe_carlo on 2006-07-16
You could try the following (I'm not sure it will help). In /etc/rc2.d, you should find a file called "S<NR>Sendmail". The <NR> indicates when sendmail needs to be started. Try renaming the file into S99Sendmail, which should postpone sendmail startup, hopefully until after the root file system gets mounted writable. Do the same in rc3.d too.

---

