---
title: "Java PATH setting?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by The Rockologist on 2006-08-20
Hey all, I'm brand new to Ubuntu, a n00b if you will, having switched over from Knoppix 3.9 for a little while to try something new. I installed 6.06 on my hard drive and added some packages and whatnot, but now I'm stuck: How do I set the Java PATH?

I installed the JDK 1.5 binary file in my home folder, but now I have no idea what to add to /etc/profile to use JDK's Javac and Java! 

A little help here? It'd be appreciated greatly! Java is basically all I do on my computers, so without it, I'm stuck! :confused:

---

### Post by hopstah on 2006-08-20
try this and hit the number of the java that you want your system to use
```
sudo update-alternatives --config java
```

---

### Post by The Rockologist on 2006-08-20
Well actually I tried that, and it didn't give me any alternatives for my particular JDK.

I have my JDK in /home/max/jdk/jdk1.5.0_04, it didn't display any of that. ):

Is there something I can actually add to /etc/profile to change that? See I'm used to Debian, which already has all this extra stuff added for you, and I was surprised Ubuntu's Profile file was so empty, what with it being based on Debian and all.

I guess basically when I enter "which javac" I need it to say "/home/max/jdk/jdk1.5.0_04/bin/javac", and "/home/max/jdk/jdk1.5.0_04/bin/java" and so on.

---

