---
title: "Java plugin Failure Lucid Lynx"
date: 2010-12-19
forum: Desktop Environments
---

### Post by kayve on 2010-12-19
I have Lucid Lynx 10.04 LTS and I am having problems with my Java browser plug in.  I want to make a certain java web app work (applet_not_initialized.jpg) and I don't know if this is telling, but one thing I tried was the graphical Ubuntu Software Center and there is no install button for Java plugins (No_Sun_Java.jpg).

Here is the output for the apt-cache search jdk

```

root@kayve-laptop:~/apt-gets# apt-cache search jdk
cacao-source - Source for CACAO, a Java virtual machine
default-jdk - Standard Java or Java compatible Development Kit
default-jdk-builddep - Standard Java or Java compatible build dependencies
default-jdk-doc - Standard Java or Java compatible Development Kit (documentation)
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
gcj-4.4-jdk - gcj and classpath development tools for Java(TM)
gcj-jdk - gcj and classpath development tools for Java(TM)
libcommons-lang-java - Extension of the java.lang package
libcommons-lang-java-doc - Extension of the java.lang package
libpg-java - Java database (JDBC) driver for PostgreSQL
libslf4j-java - Simple Logging Facade for Java
mauve - free test suite for the Java Class libraries
fakeroot-ng - Gives a fake root environment
freemind - Java Program for creating and viewing Mindmaps
japitools - Java API compatibility testing tools
java3ds-fileloader - Java3D 3DS FileLoader
libcommons-launcher-java - cross platform java application launcher
libcommons-math-java - Java lightweight mathematics and statistics components
libcommons-math-java-doc - Java lightweight mathematics and statistics components - documentation
libhibernate-annotations-java - Hibernate Annotations
libhibernate-commons-annotations-java - Hibernate Commons Annotations
libicu4j-java - Library for unicode support and internalisation
libitext1-java - Java Library to generate PDF on the Fly
libjboss-aop-java - JBoss Aspect Oriented Programming (AOP) framework
libjboss-common-java - The JBoss Common Project
libjboss-marshalling-java - alternative serialization API
libjxp-java - Java template engine/script processor
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libpicocontainer-java - Java library implementing the Dependency Injection pattern
librxtx-java - Full Java CommAPI implementation
libtrove-java - high performance collections for java
libtrove-java-doc - high performance collections for java
libwagon-java - tools to manage Maven artifacts and deployment
mmake - Makefile generator for Java programs
substance - cross-platform look & feel for Swing applications
substance-doc - cross-platform look & feel for Swing applications - documentation
testng - testing framework for Java
usepackage - utility to manage environment variables from within dotfiles
jde - JDEE, Java Development Environment for Emacs(en)
icedtea-6-jre-cacao - Alternative JVM for OpenJDK, using Cacao
icedtea6-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
openjdk-6-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-6-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-6-doc - OpenJDK Development Kit (JDK) documentation
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-6-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-6-source - OpenJDK Development Kit (JDK) source files
openoffice.org-gcj - office productivity suite -- Java libraries for GIJ
openjdk-6-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark
openoffice.org - office productivity suite
visualvm - All-in-One Java Troubleshooting Tool

```It says I have icedtea6-plugin and I thought that was supposed to let my browsers work right, but neither Opera nor Firefox can make the monkeyview java applet work.  

and here is java -version

```

root@kayve-laptop:~/apt-gets# java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu1~10.04.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)


```Can anyone help me fix my environment so my browsers can operate the monkeyview upload applet?  Monkeyview.net is a free photoserver if anyone felt like testing the upload applet themselves, they can create their own account to do so.  Thank you very much in advance for any help.

---

### Post by innovativeinfosln on 2010-12-20
I ran into a similar issue yesterday when I installed Ubuntu Lucid Lynx Beta 2. However, the default install didn't give me either OpenJDK or IcedTea. To get Java, I had to enable the partner repositories (I did it via Synaptic Package Manager just because I'm lazy), Sun Java6 then showed up, I installed it, and that was it. I didn't have to set any alternatives because that was the only Java install on the system.

[Web Development Edina]("http://www.innovativeinfosolutions.com")
[http://www.innovativeinfosolutions.com]("http://www.innovativeinfosolutions.com")

---

### Post by kayve on 2010-12-20
ok I'm not sure what you mean by "partner"

is this it?

---

### Post by ImDougy on 2010-12-20
open  ubuntu software center, click edit, click software sources from the dropdown menu, click other software tab, and check canonical partners and canonical partners (source code). hope that helps:grin:

---

### Post by ImDougy on 2010-12-20
ooooor open synaptic package manager, click settings, click repositories, click other software tab, check canonical partners and click close. but firefox or any other browser you are using will use openjdk by default so what i do is uninstall openjdk and then try it. don't worry when an application needs openjdk it will install itself.

---

