---
title: "Changing the OpenJDK temporary files directory"
date: 2009-06-05
forum: General Help
---

### Post by siryuhan on 2009-06-05
When I first ran a java application, OpenJDK asked for a directory (it selects /tmp as default) to store files. I would like to change this directory but I cannot find the appropriate configuration file or settings window. Assistance is greatly appreciated. Thanks!

---

### Post by Yellow Pasque on 2009-06-05
Look in your home directiory for a hidden file/directory - .openjdk
Or maybe a system-wide configuration file/directory in /etc

---

### Post by siryuhan on 2009-06-05
I seem to have found the answer. The configuration file is located at ~/.netxrc

---

