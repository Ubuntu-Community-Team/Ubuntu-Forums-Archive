---
title: "update-alternatives for java"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-07-13
I have a little question, I installed java but I think it isn't configured correctly in /etc/alternatives/, this is the output of "sudo update-alternatives --config java", which one should I choose? (I think the last one but I want to be sure)
```
There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/local/jre1.5.0_06/bin/java
 +    2        /usr/lib/j2se/1.4/bin/java
      3        /usr/bin/gij-wrapper-4.0
      4        /usr/bin/gij-wrapper-4.1
      5        /usr/lib/jvm/java-gcj/jre/bin/java
      6        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

---

### Post by jordilin on 2006-07-13
There are two possible options, the number 1 and number 6, but it seems that the number 1 is the latest version. So I would choose number 1. It seems you installed different versions of java, did you?

---

### Post by Athropos on 2006-07-13
1 and 6 are equivalent, both are Sun's JRE. However, if you select 6, you may be able to remove your own copy of the JRE (in /usr/local). 6 is the packaged version, it will be automatically updated in the future.

---

### Post by timetunnel on 2006-07-13
Number 6 is the same java version (1.5.0.06) if you used the SUN java packages from the ubuntu repositories. 

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java 
is just a link to 
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java

So 1 or 6 should be fine. However, 1 doesn't seem to be a package from the ubuntu repository.

---

### Post by Ramses de Norre on 2006-07-13
Ow ok, and I did install my own version in breezy when it wasn't in the repos yet.
So I'll pick six and I'll see how to remove the non-repo version.
Thanks a lot ;)

---

