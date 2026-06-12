---
title: "Installing Java on 8.04 LTS"
date: 2009-01-14
forum: General Help
---

### Post by Alf Stockton on 2009-01-14
With a view to installing TRAC+, which is a Java application, on a 8.04 LTS system I have run "apt-get install sun-Java5-bin" but when it gets to actually installing TRAC+ and issuing the command
"$JAVA_HOME/bin/jar -xvf track-361.war"
in the appropriate directory I get an error:-
 -bash: /bin/jar: No such file or directory

Look as I might I cannot find the jar file anywhere on the system. So the problem is more than just not having $JAVA_HOME set.

I have obviously got the installation of Java wrong but where?

---

### Post by Tim Sharitt on 2009-01-15
jar is included in sun-java5-jdk. I'm not sure why it is noe t in the jre package. Other packages including jar are"
```

The program 'jar' can be found in the following packages:
 * java-gcj-compat-headless
 * gcj-4.2
 * sun-java5-jdk
 * kaffe
 * gcj-4.3
 * openjdk-6-jdk
 * fastjar
 * cacao-oj6-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>

```

---

