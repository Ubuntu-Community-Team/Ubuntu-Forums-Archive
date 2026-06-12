---
title: "Minecraft server won't start - SOLVED"
date: 2014-02-07
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2014-02-07
I am running xubuntu 12.04.3 and I wanted to run a LAN minecraft server so my step daughter and I could play together BUT I couldn't get it to work. I followed every ubuntu tutorial i had found out there which doesn't show anything special about installing java. I kept getting various errors from java, ranging from 
Error: Could not find or load main class minecraft_server.1.7.1.jar as well as some other errors at first that I don't recall. The command I was trying was just
```
java -Xmx512M -Xms512M minecraft_server.1.7.4.jar
```

I had first tried with using openjdk-6-jdk, default-jdk,  openjdk-7-jre and openjdk-7-jdk as that's what the tutorials were showing and I couldn't get it to work. So then I found a tutorial for using the oracle version of java from the webupd8team ppa. So I removed the openjdk-6-jdk, default-jdk, and openjdk-7-jdk packages, added the oracle java ppa, installed oracle-java7-installer and ensured I had set the java version I wanted to use with the following command
```
sudo update-alternatives --config java
```
then I enter the number that correlated to the java version from oracle. then to start the server I ran the following command from the folder I made that contained the .jar file.
```
/usr/bin/java -Xmx512M -Xms512M -jar minecraft_server.1.7.4.jar
```
I only have 1.5GB in this server so i used 512M, if you have 2 or even 4 you can run with that number at 1024 or even 2048. it's basically how much ram you're allowing the minecraft server to use.

*NOTE* Running the full java command with /usr/bin/java blh blah may have worked with just using default-jdk and openjdk-7-jdk but i didn't try it so not sure.

---

