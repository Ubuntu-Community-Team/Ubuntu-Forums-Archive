---
title: "Java/Minecraft issues"
date: 2013-04-20
forum: Gaming &amp; Leisure
---

### Post by Esselean on 2013-04-20
Here is the problem:
I had been playing minecraft from my computer using openjdk6 and it was working fine. However lately I have been having some unrelated internet issues and decided to see if I could get minecraft running in browser for when my internet connecting was being screwy. I tried for 6 hours to get a sun java plugin working as this is what is recommended by minecraft. 
After many failed attempts at getting sun java to work I went back to openjdk6 and installed icedtea plugin. Using icedtea plugin gives me a lovely blank screen when I try to play minecraft in browser.... Even better is I can no longer play minecraft from my computer now! 
I have tried doing "open with..." and using the java -jar minecraft.jar command (both of which have worked in the past) but I get absolutely zilch. Not even an error..
I am at a loss as to what else I can do!

---

### Post by Ender Shadow on 2013-04-20
Try completely uninstalling OpenJDK 6 and the java plugin that you installed and instead, install Oracle Java. *[This]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")* link should help you.

---

### Post by Esselean on 2013-04-20
Thanks. I will give it a go.

---

### Post by Horbo on 2013-04-20
> **Ender Shadow said:**
> Try completely uninstalling OpenJDK 6 and the java plugin that you installed and instead, install Oracle Java. *[This]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")* link should help you.

I don't have an answer for the OP's specific problem, but this is going to cause problems of its own.  MC doesn't like Oracle Java 7.  Oracle Java 6 is fine.  For Open Java I have no idea.

---

### Post by efflandt on 2013-04-22
Minecraft does not have any problems with openjdk-7. The only reason I installed 7 in place of 6 was because when I tried running a tekkit server some time ago, just one of the tekkit minecraft mods required it. Plain vanilla minecraft client or server (and tekkit client) should work fine with either openjdk. There could be conflicts with both openjdk and Oracle Java installed.
```
efflandt@XPS8100-1204:~$ dpkg-query -l openjdk* | grep ii
ii  openjdk-7-jre                          7u15-2.3.7-0ubuntu1~12.04.1             OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless                 7u15-2.3.7-0ubuntu1~12.04.1             OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                      7u15-2.3.7-0ubuntu1~12.04.1             OpenJDK Java runtime (architecture independent libraries)
```I don't think that I have ever gotten minecraft working in a browser in Linux. But the minecraft.jar launcher always works the customary way suggested on minecraft.net: **java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame** (although, I give it more RAM).

---

### Post by Ender Shadow on 2013-04-22
> **Horbo said:**
> I don't have an answer for the OP's specific problem, but this is going to cause problems of its own.  MC doesn't like Oracle Java 7.  Oracle Java 6 is fine.  For Open Java I have no idea.

I haven't had any problems with Oracle Java 7, and both OpenJDK 5 and 6 work okay as well.

---

### Post by Horbo on 2013-04-23
> **Ender Shadow said:**
> I haven't had any problems with Oracle Java 7, ...
Well I think you should consider yourself lucky!

I, and many others, have, consistently and repeatedly.

---

