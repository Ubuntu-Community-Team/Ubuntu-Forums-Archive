---
title: "Run .class files"
date: 2009-01-02
forum: General Help
---

### Post by arsen13 on 2009-01-02
I run .class files using terminal, but it displays the following message:
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld/class
Caused by: java.lang.ClassNotFoundException: HelloWorld.class
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: HelloWorld.class. Program will exit.

This is just a test program displaying a message, so i didn't use anything special. 
I've compiled the program using javac version 1.6.0.10 (jdk).
the programm is the following:
public class HelloWorld {
 
   public static void main(String[] args) {
      System.out.println("Hello World!");
   }
      
} 
How can I make it work? 
Thanks
-arsen13

---

### Post by Tim Sharitt on 2009-01-02
Are you running 
```
java HelloWorld.class
```
Java doesn't need the extention and including will cause an error
The correct way to run HelloWorld.class is
```
java HelloWorld
```

---

### Post by arsen13 on 2009-01-02
Thanks
 I was running using: java HelloWorld.class

---

### Post by rugsrme on 2009-01-04
I get the same error but my problem is the conflict between java -version:
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
and javac -version is:
javac 1.6.0.11

Also running sudo update-alternatives --config java
I get:
There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.


I am really out of touch, just getting back to using linux and learning java.
Any help would be appreciated.
Q

---

### Post by rugsrme on 2009-01-04
Ok, I tried typing the full path:
/usr/java/jdk1.6.0_11/bin/java sampleprog

and it worked.
How can I get the path set right to do this without typing the entire path?
Q

---

### Post by Tim Sharitt on 2009-01-05
> **rugsrme said:**
> 
How can I get the path set right to do this without typing the entire path?
Q

On my machine /bin/java is a symlink to /etc/alternatives/java which is a symlink to to the actual java installation. So, you should be able to point one of those links to the jre you want to use.

---

### Post by rugsrme on 2009-01-05
/usr/java/jdk1.6.0_11/bin/java is not a symlink and the /etc/alternative/java symlink points to:
/usr/bin/gij-wrapper-4.1

Do I dare change it to point to:
usr/java/jdk1.6.0_11/bin/java ?

---

