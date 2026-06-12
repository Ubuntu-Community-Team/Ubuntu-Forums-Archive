---
title: "Java jar question"
date: 2009-06-11
forum: General Help
---

### Post by gov cheese on 2009-06-11
Following Major League Baseball's directions, I downloaded their java jar called autobahn.jar from the MLB site.  

This is in order to run their "nexdef" Flash based service to watch games. While I can already watch their games (thanks Jaunty), I can't take advantage of the better resolution offered without the nexdef plugin.

MLB says: Linux users can, however, enjoy NexDef enabled video by downloading the autobahn.jar file, and invoking it with "java -jar autobahn.jar" on a Sun Java VM 1.4.1 or newer."

Into which file do I place this autobahn.jar, and how do I "invoke" it?

---

### Post by lamego on 2009-06-11
From the terminal just run:
```
java -jar file.jar
```

---

### Post by kuja on 2009-06-11
That file should standalone, place it wherever you like. To invoke it open a terminal and cd to the directory where you placed the file, then invoke it with the commmand they gave you.

(If you don't have java installed, you can install the sun-java6-jre package or openjdk-6-jre. After installing run "sudo update-java-alternatives -l" to see what update-alternatives is calling the one you installed, then sudo update-java-alternatives -s <whateveryoupickedhere> to set it.

---

