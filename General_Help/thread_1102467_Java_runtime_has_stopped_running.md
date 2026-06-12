---
title: "Java runtime has stopped running"
date: 2009-03-21
forum: General Help
---

### Post by v1nsai on 2009-03-21
I'm having trouble running java programs on my ubuntu box.  I was coding something for my java class, and became suspicious when my programs kept returning this when I ran 'java nameOfProgram':
```
Caused by: java.lang.ClassNotFoundException: TempTest
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: TempTest. Program will exit.
```

I get the same error when I run examples from the book.  They all have main methods, which is what the error seems to be complaining about.  Everything runs fine on Windows XP in virtualbox.

So, first of all what the hell?  Why did this happen?  I've been running java on my computer no problem for a while now.  And second, what can I do to fix this?  I've already tried 'sudo apt-get remove sun-java6-jre sun-java6-jdk' and 'sudo apt-get install sun-java6-jre sun-java6-jdk' but still the same problems.  I can compile with no hitch, it just seems to be the runtime.  Help appreciated, I'm stumped.

---

### Post by The Cog on 2009-03-21
Make sure your command prompt is running in the same directory as the class file you compiled. The command **ls** should show **TempTest.class** amongst others.

---

### Post by v1nsai on 2009-03-21
You know, I almost got really pissed off that you were actually reminding me to cd into the correct folder, but I tried 'java TempTest' in the wrong folder, and still got the same response so I guess your not calling me a space cadet lol.  I'm still getting the error whether or not I'm in the correct folder, I'm compiling without error then running java too.

Anyway, it's acting like it doesn't see the class file, that's weird.  I ran 'java -version' and it returned that its java build 1.6.0_0-b11, so as far as I can tell the jre is up and running.

---

### Post by The Cog on 2009-03-22
No offence was intended. I've done it myself. The only other things I can think of are:

That somehow your CLASSPATH environment variable is preventing you from seeing local class files, though I don't know how that might happen. Try making sure you do NOT have a CALSSPATH environment variable. 

Or the class source has a package declaration in it, such that it shoud really live in a subdirectory. Actually, I just tried this and it gives the error message you are seeing. So it a class is declared as "package brownenvelope;" for instance, it needs to be in brownenvelope/TempTest.class and launched as "java brownenvelope.TempTest".

---

### Post by v1nsai on 2009-03-22
I did add a classpath recently (I was playing around trying to cross compile java on the iphone) and got rid of it via gedit /etc/environment but I'm still getting the same error.  Do I need to restart anything to get the changes to register?  My /etc/environment file now contains only ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
It's definitely not in a package or anything like that, I used BlueJ to write it but I've always used bluej and never had problems running from shell.

---

### Post by men28 on 2009-03-22
There are number of java versions. They can be installed simultaneously.  
Errors like these you posted it seems caused if used open source version of java.
Java from Sun is most reliable.

In order to see which javas you have type in Terminal:
```
update-java-alternatives -l
```

In order to install Sun's java type:
```
sudo apt-get install sun-java6-bin sun-java6-jdk
```

In order to activate Sun's java type:
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by v1nsai on 2009-03-22
Thanks men, it looks like I was running both the openjdk and the sun-java6-jdk, I uninstalled both, then reinstalled sun-java6-bin/jdk and am now getting a slightly different error code:
```
Exception in thread "main" java.lang.NoClassDefFoundError: TempTest
Caused by: java.lang.ClassNotFoundException: TempTest
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```
The error codes are different now, I'm trying to figure out what they mean.

---

### Post by txcrackers on 2009-03-22
Sorry, but there's nothing "wrong" with Java - that exception means exactly what it says: it cannot find a class. I would seriously recommend reading the Java tutorial about ClassPaths and the like - it's really quite essential for understanding how that aspect of Java works, especially if you're programming in it.

FYI, using the CLASSPATH environment variable is usually not recommended any more - that kinda changed with Java 1.3

---

### Post by v1nsai on 2009-03-22
@ crackers, while I appreciate what I suppose we could call an attempt to help, you clearly haven't read anything I said.  I said I removed the classpath and that that might have been the cause of the problem, and I also said that since my programs ran fine under windows, there is obviously something "wrong" with my runtime and my system, not with java itself so don't get your feelings hurt.  I obviously wouldn't use it if I thought something was wrong with it.

Anyway, I still haven't figured out what's going on or found anyone else with a similar problem, I'm literally able to 'java helloWorld' in virtualbox and it runs just fine, then 'java helloWorld' in ubuntu on the exact same file and it gives me the class not found error

---

### Post by coffeexxninja on 2009-03-23
I'm having a similar problem, java won't run anything at all on my system after I used a CLASSPATH for something.  Maybe I didn't change /etc/environment back to normal, what is the default?  Mine currently only has
/etc/environment:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by coffeexxninja on 2009-03-24
Sorry for the bump, but I've been researching for days and still don't know what I'm doing wrong, I've got the exact same problems as OP, if anyone knows anything please share, I'm hoping I screwed something up and it will be easily fixed.

---

### Post by v1nsai on 2009-03-26
I got nothing either, I'm trying to find out more about /etc/environment cuz it seems like both of us messed with classpath but I still haven't found how to fix it.  It very obviously lacks a man page, someone submitted a bug report about that hopefully they'll roll one into later releases to prevent stuff like this.

---

