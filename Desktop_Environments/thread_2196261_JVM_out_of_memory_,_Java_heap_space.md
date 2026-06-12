---
title: "JVM out of memory , Java heap space"
date: 2013-12-28
forum: Desktop Environments
---

### Post by osama-salama on 2013-12-28
I checked similar Threads but java -Xmx is not working through the terminal, recognized as a unknown command, how can I change this value ?

---

### Post by pbrane on 2013-12-29
This is how I use the arguments.

```

java -Xms256M -Xmx512M -jar path/to/jar/file.jar

```

or 

```

java -Xms512M -Xmx1G -jar path/to/jar/file.jar

```

---

