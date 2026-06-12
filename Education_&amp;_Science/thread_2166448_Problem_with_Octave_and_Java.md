---
title: "Problem with Octave and Java"
date: 2013-08-09
forum: Education &amp; Science
---

### Post by lordfkiller on 2013-08-09
I have installed Octave (from repos) for the first time. I also installed the Java API package.
When I run octave from terminal, here's what I get

```
warning: timestamp on file /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server/libjvm.so is in the future
error: java_invoke: /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server/libjvm.so: failed to load: /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server/libjvm.so: cannot open shared object file: No such file or directory
error: called from:
error:   /usr/share/octave/packages/java-1.2.8/javaaddpath.m at line 41, column 13
error:   /usr/lib/x86_64-linux-gnu/octave/packages/io-1.0.19/x86_64-pc-linux-gnu-api-v48+/PKG_ADD at line 20, column 11
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error: addpath: all arguments must be character strings
error:   /usr/share/octave/3.6.4/m/pkg/pkg.m at line 2357, column 5
error:   /usr/share/octave/3.6.4/m/pkg/pkg.m at line 2147, column 1
error:   /usr/share/octave/3.6.4/m/pkg/pkg.m at line 401, column 7
error:   /usr/share/octave/3.6.4/m/startup/octaverc at line 33, column 1

```

The problem is it is looking for OpenJDK whereas I use Oracle Java. JAVA_HOME is correctly set to /usr/lib/jvm/java-7-oracle, so is PATH. 

So how can I tell Octave where to look for JRE and/or JDK?

Thanks

---

### Post by anisterra on 2013-09-25
Look in here : [http://wiki.octave.org/Java_package#How_to_make_Java_classes_available_to_Octave.3F](http://wiki.octave.org/Java_package#How_to_make_Java_classes_available_to_Octave.3F)
( I am using this wiki page for more elemental actions and find it very useful , this java chapter seems exhausive)

---

