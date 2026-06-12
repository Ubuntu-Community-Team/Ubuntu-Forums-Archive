---
title: "Bad/Low fps on Ubuntu Minecraft"
date: 2015-05-26
forum: Gaming &amp; Leisure
---

### Post by grb2 on 2015-05-26
Hello!, My name is GRB and I currently have a pc loaded with linux (ubuntu). Strangely enough when I downloaded Minecraft and opened it I didn't see my expected results. I got 7-15 fps which is really not playable at all. I have a good pc and am wondering what the problem is. I have a laptop also that gets 60-80fps and that has-

[FONT=Helvetica Neue]Processor 1.4 GHz Intel Core i5[/FONT]
[FONT=Helvetica Neue]Memory   4 GB 1600 MHz DDR3
[/FONT]
[FONT=Helvetica Neue]Graphics  Intel HD Graphics 5000 1536 MB
[SIZE=2]


My pc has a
Geforce GTX 750Ti Graphics card 2gb memory
Asus 597 Plus MotherBoard supports intel
8GB ram
And the Cpu/proccessor is good enough xD

Plz help me!


[/SIZE]Oh yes in Minecraft it is weird when I look down or am underground i get a solid 60 fps but when I go to spawn it drops to 10 fps. Also when I optifine zoom it helps the fps[/FONT]

---

### Post by QIII on 2015-05-26
Hello!

Did you install MineCraft natively or by using Wine?

---

### Post by grb2 on 2015-05-26
No I downloaded it off the minecraft.net

---

### Post by QIII on 2015-05-26
What version of Java are you using?

---

### Post by grb2 on 2015-05-26
Version 6 because version 7 and 8 won't show up on the open with

---

### Post by QIII on 2015-05-26
I would immediately remove Java 6 as it is EOL and rife with security issues.

Do you have 7 or 8 installed?  If so, you can start the Minecraft .jar.

---

### Post by grb2 on 2015-05-26
I do have the 7 and 8 JRE installed but they don't show up on the open with option

---

### Post by QIII on 2015-05-26
Can you run it from the terminal with

```
 java -jar Minecraft.jar
```

After changing your Java alternative to 7 or 8?

---

### Post by grb2 on 2015-05-26
nope says Unable to access minecraft.jar

---

### Post by QIII on 2015-05-26
Could you copy the exact message returned in the terminal and post it here?

Also, please post the results of 

```
 java -version 
```

---

### Post by grb2 on 2015-05-26
Error: Unable to access jarfile Minecraft.jar

java -version
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
openjdk version "1.8.0_45-internal"
OpenJDK Runtime Environment (build 1.8.0_45-internal-b14)
OpenJDK 64-Bit Server VM (build 25.45-b02, mixed mode)

---

### Post by brian62 on 2015-05-26
Use synaptic to install default-jre or do sudo apt-get install default-jre

---

### Post by QIII on 2015-05-27
The jar may be named minecraft.jar (but I'm pretty sure it's Minecraft.jar), or it may be in a different directory than your /home.

If you can find it, then the general way to start it would be

```
java jar /path/to/Minecraft.jar
```

---

### Post by QIII on 2015-05-27
> **brian62 said:**
> Use synaptic to install default-jre or do sudo apt-get install default-jre

This is not necessary. 

If I were to suggest anything, I would say to install Oracle Java 7 or Oracle Java 8 as described [URL="http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html"]here.

[/URL]Oracle Java 8 can be installed using the same package, but installing 

oracle-java8-installer

instead of 

oracle-java7-installer

---

### Post by grb2 on 2015-05-27
Alright guys i just installed oracle java 8 and its still not getting any better performance D:

---

