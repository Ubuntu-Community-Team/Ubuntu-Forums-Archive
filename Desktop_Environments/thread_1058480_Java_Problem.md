---
title: "Java Problem"
date: 2009-02-02
forum: Desktop Environments
---

### Post by paradoxic on 2009-02-02
I am trying to get the program JGrasp ([http://www.jgrasp.org/](http://www.jgrasp.org/)) to work properly. Right now I got the program running but I cant get the debugger to work. When I try to run the debugger I get an error that says I need JDK. I think the problem is that I have both JDE and JDK installed but I can't figure out how to point JGrasp to the right version of Java.

Any suggestions?

---

### Post by wilbbe01 on 2009-02-02
```
sudo update-alternatives --config java
```

may be of some help to you.

Also, are you sure you have jdk installed and not only jre?

---

### Post by paradoxic on 2009-02-02
I'm almost certain because all the features of JDK work in another Java editing program I have (Eclipse).

Here is the output of sudo update-alternatives --config java:
  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Also here is the output of java -version:
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

So it seems like it should be working...but it JGrasp is still not letting me debug. Is it possible that my JDK version doesnt support integrated debugging? How can I check or update it so that it does?

---

### Post by binbash on 2009-02-03
select the sun not openjdk.

---

### Post by paradoxic on 2009-02-03
I tried that and it actually made JGrasp look nicer but I am still getting the error when I try to debug. Any other suggestions?

Is there any way to manually install the debugger?

I found this on the JGrasp website, but I dont know how to do what they are saying:
> To use the integrated debugger, jGRASP must be running under the JDK (not a JRE). If you are having some problem with this (you get a "tools.jar file not on classpath" message when attempting to debug), putting the JDK bin directory at the beginning of the PATH should fix this. For a detailed description of how the jGRASP startup programs find/choose java, see Running jGRASP. 

Heres some more info I found:
> For both the Windows and UNIX/Linux startup programs, to use the integrated Java debugger, "java.exe" or "java" must be in the JDK directory structure (in /bin, where tools.jar is in /lib), unless the "-cp" command line argument or JGRASP_CLASSPATH environment variable is used. 

But how can I check for this?

---

### Post by paradoxic on 2009-02-03
Bump

---

