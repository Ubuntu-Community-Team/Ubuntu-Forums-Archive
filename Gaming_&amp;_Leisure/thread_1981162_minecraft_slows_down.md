---
title: "minecraft slows down"
date: 2012-05-16
forum: Gaming &amp; Leisure
---

### Post by KG4UJD on 2012-05-16
I am running the newest version of minecraft on ubuntu 11.10 and after about 5 minutes or so it starts to slow down and not respond to commands

---

### Post by regor210 on 2012-05-16
If you have 1Gig or less of ram on your motherboard Minecraft may be using swap memory. In other words your system is trying to use your hard drive to store ram memory that should be stored on the mother boards system ram. for gaming this is very slow.  start Minecraft like this if its an issue.    

To open a terminal press ctrl+alt+t then cut and paste the following commands into the terminal window one line at a time minus the $.

$  java -Xmx256M -Xms256M  -cp minecraft.jar net.minecraft.LauncherFrame

This assumes  minecraft.jar is in your home folder.

---

### Post by phYnc on 2012-05-17
Are you using openjdk 7?
 
```
 
sudo apt-get remove openjdk6 icedtea-6-plugin
sudo apt-get install openjdk7 icedtea-7-plugin

```
 
I'm not experiencing the slow down problems.

---

### Post by ELD on 2012-05-18
We really do need more info, on posts wanting help try including system specs and explain how you are running the game, using what commands.

---

### Post by roh8880 on 2012-06-07
I tried your suggestion of switching to OpenJDK7 from the terminal, but terminal said it couldn't find the package.

```
ghost@ghost:~$ sudo apt-get install openjdk7 icedtea-7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openjdk7
ghost@ghost:~$ 

```

Running 10.04 LTS

---

### Post by Majorix on 2012-06-07
I thought Ubuntu uses OpenJDK by default anyway?

The problem in your case, I guess, is some sort of memory leak caused not by you, but by the way the JRE is built. I don't run Java apps on systems I have to keep responsive. It doesn't matter if it is Linux, Windows or *BSD. I seriously hope they find a fix.

/rant :)

---

