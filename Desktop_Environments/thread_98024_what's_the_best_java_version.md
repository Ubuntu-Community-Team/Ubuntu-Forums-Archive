---
title: "what's the best java version?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by dabear on 2005-12-02
«sudo update-alternatives --config java» java gives me
```

      1        /usr/lib/jvm/java-gcj/bin/java
      2        /usr/bin/gij-wrapper-4.0
*+    3        /usr/lib/j2se/1.4/bin/java
      4        /usr/local/jre1.5.0_05/bin/java
      5        /usr/lib/j2re1.5-sun/bin/java
      6        /usr/lib/j2sdk1.5-sun/bin/java

```
What's the best of them, and which takes up less memory?

---

### Post by veelivar on 2005-12-02
I'm not sure about memory consumptions but if your not wanting to write your own code then go for 

4        /usr/local/jre1.5.0_05/bin/java
or
5        /usr/lib/j2re1.5-sun/bin/java

I'm not sure what the difference is between thses two.

1.5 is the latest and I believe it is supposed to be faster than 1.4.2


Dan.

---

