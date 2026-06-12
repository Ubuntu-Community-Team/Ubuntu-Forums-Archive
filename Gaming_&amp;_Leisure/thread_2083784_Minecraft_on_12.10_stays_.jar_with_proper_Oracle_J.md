---
title: "Minecraft on 12.10 stays .jar with proper Oracle Java installation"
date: 2012-11-13
forum: Gaming &amp; Leisure
---

### Post by Oral B Sonic Complete on 2012-11-13
Hey,

I followed this [Guide]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") to install the Java JDK on my laptop. I chose the JDK over the JRE, because i might need it later on.... Anyway, i thought i could play some Minecraft now. 

Turns out i can't, because the Minecraft executable still has that image of a packet, and when i doubleclick on it, it gets extracted. 

java -version gives me this: 

```
java version "1.7.0_09"
Java(TM) SE Runtime Environment (build 1.7.0_09-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.5-b02, mixed mode)

```

I'd appreciate your help. :) thanks...

---

### Post by jerome1232 on 2012-11-13
You just have archive manager set as the default program to open jar files. Right click it (minecraft.jar), select properties, select the open with tab, Select Oracles java, click set as default, and close it out.

Now double clicking should work. If you get a black screen there is a work around for it, let me know if that happens.

Edit, I looked at your guide, and highly recommend following this guide: [https://help.ubuntu.com/community/Java#Installing_Oracle_Java_7_by_a_script_or_from_the_command_line](https://help.ubuntu.com/community/Java#Installing_Oracle_Java_7_by_a_script_or_from_the_command_line)

Click on [Using webupd8.org's strikingly simple method.]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")
That method will keep java up to date in addition to being extremely easy. It's up to you if you want to go through the trouble of undoing what you did or not.
[]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

---

