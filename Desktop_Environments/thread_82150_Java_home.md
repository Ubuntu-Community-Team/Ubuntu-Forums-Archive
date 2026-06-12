---
title: "Java_home?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by rj686 on 2005-10-26
ok i download jre and jdk straight from sun and made deb packages (fakeroot) and installed them. now i changed my JAVA_HOME but still it gives me the old version of java when i type "java -version"

---

### Post by RAOF on 2005-10-26
Have you run "sudo update-alternatives --config java" and selected the sun runtime?

---

### Post by rj686 on 2005-10-26
thx :) is java version pertaining to jre er jdk?

---

### Post by RAOF on 2005-10-26
The jre.  But if you installed the jdk, they'll have the same versions.

---

