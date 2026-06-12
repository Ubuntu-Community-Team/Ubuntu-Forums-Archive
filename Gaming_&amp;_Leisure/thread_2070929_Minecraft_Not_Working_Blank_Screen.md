---
title: "Minecraft Not Working Blank Screen"
date: 2012-10-14
forum: Gaming &amp; Leisure
---

### Post by T31337 on 2012-10-14
When i try to play minecraft classic after it downlaods files it sits at a blank black screen. I have tried updating my lwjgl as suggested in [http://ubuntuforums.org/showthread.php?p=12288945](http://ubuntuforums.org/showthread.php?p=12288945) but even after updating lwjgl minecraft still will not work.
[LEFT]:confused:

[/LEFT]

---

### Post by mentorious on 2012-10-14
Always after update you must replace the lwgj libs ("natives" and jinput.jar, lwjgl.jar, lwjgl_utils.jar). 

Yes, it's toilsome. I makes a copy of "bin" (except minecraft.jar file) and then update.

Blank screen appears when use you OpenJDK 6/7,  try delete them and install "SunJava 6". If you will of course )

---

### Post by T31337 on 2012-10-14
tried installing sunjava6(and currently have it installed) that and it did not work for me I still get blank screen.. when I had only sun java6 installed mozilla did not ask me to run java applet just gave me blank screen with small white bar at bottom left of screen I am still unable to play minecraft classic(i can download and run new demo world jar file just fine)

---

### Post by mentorious on 2012-10-15
Check your Java runtime here: [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp)

I use  Java 7 and everything works (Minecraft Classic, Minecraft 1.3.1 Full). 

First remove  via synaptic every package which cointans 'openjdk'. 

Then install Java:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install oracle-java7-installer iceadtea-7-plugin
``````
mkdir ~/.mozilla/plugins
ln -s /usr/lib/jvm/jdk1.7.0_04/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins
```works fine [http://screencloud.net/v/m6ZV](http://screencloud.net/v/m6ZV) :)

---

### Post by T31337 on 2012-10-15
when i run the first command i get this output in terminal:
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~webup/+archive/ppa](https://launchpad.net/api/1.0/~webup/+archive/ppa)

the java check tells me i have oracle java se7 update7

---

### Post by T31337 on 2012-10-25
Installed sun-java6 and sun-java-plugin and removing openjdk after clicking "run" on java applet for minecraft classic after dowloading packages i get a blank balck screen... :(

---

### Post by T31337 on 2012-10-28
Uninstalled sun-java and installed oracle8 now minecraft classic works for me :)

---

