---
title: "can't install froswire"
date: 2006-07-29
forum: Desktop Environments
---

### Post by jman623 on 2006-07-29
I already tried automatix and I even tried chaning the the JAVADIR variable in the Run frostwire shell script to the directory where java is installed and i stil get this output:
```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com [java = ]
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/jre1.5.0_07/bin/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/jre1.5.0_07/bin/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory

```

any ideas?:confused:

---

### Post by croak77 on 2006-07-29
Did you try:

sudo update-alternatives --config java

---

