---
title: "Cannot play minecraft :("
date: 2012-11-24
forum: Gaming &amp; Leisure
---

### Post by iWinston on 2012-11-24
Hello, i cannot play minecraft on my 12.10 ubuntu. when i try to open the game i get the error: no JVM could be found on your system. But when i open termial and type: 

java -version

it comes up:

java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.10.1)
OpenJDK Server VM (build 23.2-b09, mixed mode)

---

### Post by yellowwinner on 2012-11-24
Go to ubuntu software center>type java>Make sure you have openJDK Java if it says you dont install it>right click mine craft.jar>permissions>Allow exutable file as a program>open whith>show more applications>openJDK <version>(NOT POLICY TOOL)
then X out and run mine craft.jar>Enjoy your awesome game:P:)

---

### Post by iWinston on 2012-11-24
> **yellowwinner said:**
> Go to ubuntu software center>type java>Make sure you have openJDK Java if it says you dont install it>right click mine craft.jar>permissions>Allow exutable file as a program>open whith>show more applications>openJDK <version>(NOT POLICY TOOL)
then X out and run mine craft.jar>Enjoy your awesome game:P:)

Thanks for the reply, firstly i have JDK installed but it does not show up when i click on show more applications 
[http://lookpic.com/O/i2/1583/qAWLBl0S.png](http://lookpic.com/O/i2/1583/qAWLBl0S.png)

---

### Post by wildmanne39 on 2012-11-24
*Thread moved to **Gaming & Leisure**.*

---

### Post by pompado on 2012-11-24
This will solve your issue ...

```
sudo apt-get install default-jre
sudo apt-get install icedtea-7-plugin
```

Now you can run minecraft with out any worries ...

Cheers

EDIT:

I also try install java with software center and minecraft did not work - but when i run does apt-get commands in the terminal - then after minecraft work ...

---

