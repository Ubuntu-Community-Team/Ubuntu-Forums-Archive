---
title: "java environment variable"
date: 2009-06-05
forum: General Help
---

### Post by candeller on 2009-06-05
Hello.

I am having a problem with setting a JAVA_HOME environment variable. I have tried adding it in numerous places:


```
# added in /home/komp/.bashrc
# added in /etc/profile
# added in /etc/environment
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.13
```All of the ways seem to work. When I type $JAVA_HOME in my terminal it points me to the directory.

However, when I try to compile a program I get this:

```
BUILD FAILED
/usr/local/OpenGTS/build.xml:323: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-openjdk/jre"
```The error output is correct, because the javac compiler resides here:
```
/usr/lib/jvm/java-6-sun-1.6.0.13
```I tried googling around and I wasn't able to find a definite answer on how to add the environment variable properly on ubuntu/linux.

It seems that "/usr/lib/jvm/java-6-openjdk/jre" directory is stored somewhere, and I just cant find where and how to change it.

I would greatly appreciate help, thanks!

---

