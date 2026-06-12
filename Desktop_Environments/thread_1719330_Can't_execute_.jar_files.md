---
title: "Can't execute .jar files?"
date: 2011-04-01
forum: Desktop Environments
---

### Post by metrogdor22 on 2011-04-01
I'm trying to execute a .jar file(SwingTest.jar). I change the directory to where the .jar is(Desktop). Then type the following EXACTLY:

java -jar SwingTest.jar

But all it outputs is:

Failed to load Main-Class manifest attribute from
SwingTest.jar

What am I doing wrong?

---

### Post by Jose Catre-Vandis on 2011-04-01
Have you installed java? You have a choice either Oracle's / Sun's Java or the open source in the repos. It is not installed by default.

Where are you typing "the following EXACTLY" ? In a terminal?

Check java is working OK:
[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

---

### Post by metrogdor22 on 2011-04-02
> **Jose Catre-Vandis said:**
> Have you installed java? You have a choice either Oracle's / Sun's Java or the open source in the repos. It is not installed by default.

Where are you typing "the following EXACTLY" ? In a terminal?

Check java is working OK:
[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

In the terminal. Yes, I do have Java installed. I can compile the .class into a .jar, but I just can't launch the .jar. Typing "java -version" into the terminal returns:

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9) (6b20-1.9-0ubuntu1)
OpenJDK Client VM (build 17.0-b16, mixed mode, sharing)

---

### Post by wolfen69 on 2011-04-02
Simply right click the .jar file>properties>permissions tab>then check off the "make executable" button. Then go to "open with" tab and select java. Then you will be able to run it by clicking the .jar file.

---

### Post by metrogdor22 on 2011-04-02
> **wolfen69 said:**
> Simply right click the .jar file>properties>permissions tab>then check off the "make executable" button. Then go to "open with" tab and select java. Then you will be able to run it by clicking the .jar file.

There is no "make executable" button in the permissions tab.

---

### Post by Morbius1 on 2011-04-02
I don't think this is a case of it being "executable" or not because the "java -jar" in :```
java -jar SwingTest.jar
``` circumvents the the way Ubuntu prevents you from running a jar file directly.

I think it's something about that jar file. The error message has nothing to do with permissions it has to do with the internal workings of the jar file itself:
> Failed to load Main-Class manifest attribute from
SwingTest.jar
I'm not a developer so don't ask me for help but is this something you created or is it something you downloaded?

---

### Post by metrogdor22 on 2011-04-02
> **Morbius1 said:**
> I don't think this is a case of it being "executable" or not because the "java -jar" in :```
java -jar SwingTest.jar
``` circumvents the the way Ubuntu prevents you from running a jar file directly.

I think it's something about that jar file. The error message has nothing to do with permissions it has to do with the internal workings of the jar file itself:
I'm not a developer so don't ask me for help but is this something you created or is it something you downloaded?

I created it. I know it's not a problem with the .jar file, as I can run it perfectly in Eclipse.

---

### Post by areeda on 2011-04-03
> **metrogdor22 said:**
> I created it. I know it's not a problem with the .jar file, as I can run it perfectly in Eclipse.
I don't use Eclipse, I use NetBeans so I'm not sure if you need to do something special to identify the Main Class.

The error message means either the manifest file or the class is missing the Main class.

To figure out which you can do jar -xvf SwingTest.jar (you probably want to do that in a temporary directory because it will extract all files from the jar).

Examine the file META-INF/MANIFEST.MF

There should be a line like:

Main-Class:  <package name>.<class name>

That matches your program.

Joe

---

