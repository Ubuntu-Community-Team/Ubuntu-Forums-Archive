---
title: "Minecraft on Ubuntu 12.04"
date: 2012-03-22
forum: Gaming &amp; Leisure
---

### Post by ELD on 2012-03-22
I know it's a pre-release Ubuntu but is there any way to get proper Java easily on it to play Minecraft?

---

### Post by ranger1021994 on 2012-03-23
> **ELD said:**
> I know it's a pre-release Ubuntu but is there any way to get proper Java easily on it to play Minecraft?

Let it stabilize first.....Or else you would end up messing your system :)

---

### Post by regor210 on 2012-03-23
Minecraft recommends Sun Java 6. Ubuntu 12.04 beta uses Openjdk-7. Minecraft works well with Oracle java 7 but you have to update LWJGL.

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

Minecraft may work using  Openjdk-7 if you  update LWJGL. But I have yet to try it.

Or you could use a PPA. I haven't tried this one my self. As aways there is a security risk in using none Ubuntu repositories. And some just do not work or installs incompatible or broken packages.....  

[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

If you do use this PPA, If it were me I wouldn't use 

******$ sudo apt-get purge openjdk*  *******

I would try this 

$ sudo add-apt-repository ppa:eugenesan/java
$ sudo apt-get update
$ sudo apt-get install oracle-java7-installer


Choosing the default Java to use
If your system has more than one version of Java, configure which one your system uses be entering the following command in a terminal window 
$ sudo update-alternatives --config java

[https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use](https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use)

This way if you don't like like oracle-java7 its easy to change back.

---

### Post by Haakon_KL on 2012-03-25
In 11.10, OpenJDK7 worked just fine.

I also got the Oracle version.

I don't want to go back to version 6 though.
Just stuff like Map<String, Collection<Something>> = new HashMap<>(); makes me cry whenever I have to go back. :(

Still, you can always just grab version 6 here:
[http://java.com/en/download/linux_manual.jsp?locale=en](http://java.com/en/download/linux_manual.jsp?locale=en)

That should work just fine.

---

