---
title: "Exception in thread &quot;main&quot; java.lang.UnsupportedClassVersionError:"
date: 2006-01-08
forum: General Help
---

### Post by k_smolka on 2006-01-08
Can anyone please explain what this java error message means

i get this error while trying to run a .jar file with the following command

java -jar filename.jar

Exception in thread "main" java.lang.UnsupportedClassVersionError:

many thanks

karl

---

### Post by vellvisher on 2008-01-13
I had the same problem. I think it is due to different versions of JVM installed.

sudo update-alternatives --config java

sudo update-alternatives --config javac

Enter these commands and select the appropriate versions.

Hope it works!

---

