---
title: "Problem Installing ChemAxon's marvinbeans"
date: 2009-02-17
forum: Education &amp; Science
---

### Post by ibeetalk on 2009-02-17
I am a chemist trying to download marvinsketch for my chemical structures drawing/presentation needs. After downloading the installation package, they provide a link that fives the following instructions for installation.

I should mention that I am a newbie in linux and have no idea whats going on really.


 [COLOR="Red"]Linux / Solaris Instructions

      Instructions
         1. After downloading, open a shell and cd to the directory where you downloaded the installer.
         2. At the prompt type: sh marvinbeans-VERSION-linux.sh
         3. After the installation, add the bin subdirectory of the Marvin Beans directory to the PATH to be able to run Marvin applications from any directory. 
      Notes
          o You need to install a Sun's Java Runtime Environment 1.4.2 (or later). You can download it from Sun's Java web site or contact your OS manufacturer.
          o If the installer does not start, check whether JAVA_HOME/bin is in PATH (where JAVA_HOME is the directory of Java).
            To chech it, type the "which java" command that shows the location of the java launcher. You should get something like this:

            /usr/java/j2sdk1.4.2_04/bin/java

            If java is missing from PATH, you will see something like that:

            /usr/bin/which: no java in (/usr/java/j2sdk1.4.2_04/bin:/opt/apache-ant-1.6.1/bin:/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin:/home/vertset/bin)[/COLOR]

I followed the protocol provided but when I typed  **sh marvinbeans-5_1_04-linux.sh** I got the error below.

[COLOR="Blue"]No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.4.2.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/kipchirchir/.install4j
[/COLOR]

What should I do? Thank you in advance.

---

### Post by ibeetalk on 2009-02-18
After searching online, I found similar problems and here are answers to questions I anticipate some of you may ask.

kipchirchir@kitale:~$ whereis java
java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz

kipchirchir@kitale:~$ which java
/usr/bin/java


kipchirchir@kitale:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

---

### Post by ibeetalk on 2009-02-23
I found a solution to my own problem! A solution within ...

So, I mentioned that I am new in Linux and dont want to do things that I am not comfortable with yet, Like deleting files and such. It turns out, the problem above can just be solved by deleting the JVM cache file. In my case, I deleted this file /home/kipchirchir/.install4j. (I actually moved it to a deferent location, just in case I needed to retrieve it).

This was the initial error I got:

No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.4.2.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/kipchirchir/.install4j

So I ran this command  **mv .install4j ./Documents** to move it from my home directory to my Documents directory.

Then I installed marvinbeans using this command

**sudo sh marvinbeans-5_1_04-linux.sh**


Followed instructions that followed and everything worked fine!

---

