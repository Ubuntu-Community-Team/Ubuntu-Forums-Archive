---
title: "Problems with NetBeans 8.1 on  Ubuntu 15.04"
date: 2016-10-01
forum: Desktop Environments
---

### Post by eightbits2010 on 2016-10-01
Downloaded JTK8 and NetBeans. It installs but has errors when executing the program.
 At his point, not sure how to fix the problem.
 
 
 When loading I get the following error:
  “The package containing the class javax.swing.JcomponentBeaninfo was not loaded.”
 
 
 I think I didn't reference the location to JTK and thought NetBeans would/could find it.
 I installed NetBeans 8.1 (it was a script file).
 
 
  I had already installed java version "1.8.0_101"
 Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
 Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
 And Java 8 was installed using the following:
 
 
 Steps to install JTK8 (this worked for the Ubuntu PC)
 
 
 $ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)

$ sudo apt-get install oracle-java8-set-default

The PC is Ubuntu 15.04 
 
 Now, I am stumped. I am hoping to get this working!

---

