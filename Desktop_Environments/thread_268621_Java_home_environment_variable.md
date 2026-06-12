---
title: "Java home environment variable"
date: 2006-09-30
forum: Desktop Environments
---

### Post by adamthompson on 2006-09-30
I am trying to use an application called Merchant of Venice. When I try to run it, I get the error message, "JAVA_HOME environment variable is not set. This should be set to the installation directory of java." The relevant line in venice (the shell?) is, "$JAVA_HOME/bin/java -jar venice.jar" What should I change this to in order to work on Ubuntu Linux? Thanks.

---

### Post by divague on 2006-09-30
try this in a terminal

sudo update-alternatives --config java

and select number 3

---

### Post by Gotterdammerung on 2006-09-30
Thanks! It helped me here also.

---

### Post by adamthompson on 2006-09-30
Unfortunately that doesn't help at all. I get exactly the same error message.

---

