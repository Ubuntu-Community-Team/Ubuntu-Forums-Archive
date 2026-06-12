---
title: "can't set java as default"
date: 2009-05-31
forum: General Help
---

### Post by BoobsLover on 2009-05-31
I created a directory /opt/java and i've installed jre1.6.0_13 (64bit),but for some reason i can't set as default and this error appears:

```
kladionica@klad1:~$ sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_13/bin/java" 1
kladionica@klad1:~$ sudo update-alternatives --set java /opt/java/jre1.6.0_13/bin/java
Using '/opt/java/jre1.6.0_13/bin/java' to provide 'java'.
kladionica@klad1:~$ java -version
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

```

:???:

---

### Post by BoobsLover on 2009-05-31
i've also tried installing java from  the repos ,same problem.

---

