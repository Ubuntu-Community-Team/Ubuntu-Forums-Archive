---
title: "BlueJ with openJDK"
date: 2008-10-07
forum: Desktop Environments
---

### Post by J1Bunny on 2008-10-07
so, i've got the most current version of java, and i've got the bluej installer.  when i right click the bluej package and hit "open with openjdk java 6 runtime", it takes me to the install pane.  however!  when i try to direct it to the jdk (/usr/lib/jvm/java-6-openjdk), it says that this is an invalid file.  

is this the appropriate file?  or do i need something else?

java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

thanks.

---

### Post by namdung on 2008-12-20
> **J1Bunny said:**
> so, i've got the most current version of java, and i've got the bluej installer.  when i right click the bluej package and hit "open with openjdk java 6 runtime", it takes me to the install pane.  however!  when i try to direct it to the jdk (/usr/lib/jvm/java-6-openjdk), it says that this is an invalid file.  

is this the appropriate file?  or do i need something else?

java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

thanks.

I wasn't myself able to install BlueJ with OpenJDK. Remove OpenJDK and install sun-java6-jdk from synaptic manager. BlueJ should autodetect Java and install. You might want to change the install folder to some other place like /opt/bluej

---

