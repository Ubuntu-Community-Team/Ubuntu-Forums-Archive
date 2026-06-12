---
title: "yahoo spades java"
date: 2009-02-10
forum: General Help
---

### Post by jwftm33 on 2009-02-10
I need some help with yahoo games. I installed 7.10 and then upgraded to hardy 8.04. I downloaded JRE and have tried a whole bunch of different fixes, but I still have a problem when I go to Yahoo Spades and enter a room. I can sit at a table and play the game but as soon as I leave the table or am booted from table I am kicked out of the room and get a message saying Applet ygames_applet bail. PLEASE help me with a fix.

---

### Post by jespdj on 2009-02-10
What version of Java are you using and how did you install it?
```
java -version
```
Try Sun Java 6:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by jwftm33 on 2009-02-10
I have build 1.6.0_07-b06 installed. I i tried your apt and it says Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.\

But i still get a applets ygamesapplet bail message when i try and go to another table. I have tried the restricted the mediunbuntu and all kinds of apts. still no fix

---

