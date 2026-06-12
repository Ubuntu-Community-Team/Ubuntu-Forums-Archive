---
title: "netbeans won't run due to java configuration"
date: 2009-01-25
forum: General Help
---

### Post by Java Geek on 2009-01-25
Hello, I have a class that requires me to use Sun's JDK not openJDK. However, when I uninstalled (using synaptic) openJDK, suddenly my netbeans won't start and it gives me this error:
```
Cannot find java. Please use the --jdkhome switch.
```

How do I reconfigure my JDK so that it will run netbeans

---

### Post by taurus on 2009-01-25
You need to install Sun's java first before you can use it.

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by Java Geek on 2009-01-25
Yes I've already done that. I believe the problem is that the $JAVA_HOME variable is not yet set.

The output of echo $JAVA_HOME is blank. How do you set up the variable?

---

### Post by taurus on 2009-01-25
You can edit your ~/.bashrc

```
gedit ~/.bashrc
```
and set it in there.

```
$JAVA_HOME=/path_to_java_bin_directory
```
But what are the outputs when you run these two commands from a terminal?

```
java -version
sudo update-alternatives --config java
```

---

### Post by Java Geek on 2009-01-25
These are the outputss before configuring.
```

stephen@stephen-desktop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
stephen@stephen-desktop:~$ 

```

```

stephen@stephen-desktop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

```

---

### Post by Java Geek on 2009-01-25
> **taurus said:**
> You can edit your ~/.bashrc

```
gedit ~/.bashrc
```
and set it in there.

```
$JAVA_HOME=/path_to_java_bin_directory
```


Even after adding this line in, echo $JAVA_HOME still returns as an empty line.

Edit: after reinstalling openjdk, Netbeans runs perfecly! WHY?

---

### Post by Java Geek on 2009-01-25
This thread is SOLVED

---

