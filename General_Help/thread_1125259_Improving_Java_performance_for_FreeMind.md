---
title: "Improving Java performance for FreeMind"
date: 2009-04-14
forum: General Help
---

### Post by linuxvacuum on 2009-04-14
I use FreeMind a lot and I want to improve its performance by increasing the peformance of Java JRE. How is that possible?

---

### Post by askreet on 2009-04-14
This isn't a direct answer, but at my work we use FreeMind in production for our support team to quickly find answers to issues.  We stopped using the Java Applet in favor of a Flash plugin, for performance reasons.  You may want to look into this alternative. :)

HTH,
askreet

---

### Post by John Cheng on 2009-04-14
If you are not already using Java 6, download it and use it ([http://java.sun.com/javase/downloads/?intcmp=1281](http://java.sun.com/javase/downloads/?intcmp=1281)).

There isn't too much you can do to improve the "speed" of the JVM. What may help is to reduce the pause from garbage collection with this option:

-XX:+UseConcMarkSweepGC

e.g., java -XX:+UseConcMarkSweepGC <freemind Main class>

---

### Post by linuxvacuum on 2009-04-14
I upgraded my JRE to 1.6.0_13-b03.

I had 1.6.0_10 before, the one with Ubuntu Intrepid Idex 8.10. Now the speed has dramatically improved! I would say it is about 2 times faster. It's incredible I can scroll all over my mindmap quickly without problems now. This is great!

---

