---
title: "Robocode on 12.04 Java problem"
date: 2012-05-18
forum: Gaming &amp; Leisure
---

### Post by Cukkimo on 2012-05-18
Hi!

I have a problem running robocode on 12.04
It won't open it and when I try to "robocode" on terminal it gives an error:

E: Cannot find JRE, exiting..

java -version outputs:

java version "1.7.0_04"
Java(TM) SE Runtime Environment (build 1.7.0_04-b20)
Java HotSpot(TM) 64-Bit Server VM (build 23.0-b21, mixed mode)

I've tried to install java with many different tutorials and nothing seems to work. Im running out of ideas. Any help?

---

### Post by Erik1984 on 2012-05-18
Have you looked at this?

[http://robowiki.net/wiki/Robocode/FAQ#Installing_and_using](http://robowiki.net/wiki/Robocode/FAQ#Installing_and_using)
[http://robowiki.net/wiki/Robocode_Download_And_Install](http://robowiki.net/wiki/Robocode_Download_And_Install)

> Ubuntu/Debian users could run into a couple of snags while installing  Robocode. The best place to install it at is your ~/ directory (which  is /home/account_name/ in short hand). 
If you have a working java compiler already, you should be set.  If not, you need to get a package from the repositories with the javac  program in it, or let Robocode install Jikes. If you changed your JDK  recently (like sun-java5-jdk to sun-java6-jdk or openjdk-6-jdk), you need to run sudo update-alternatives --auto javac in your shell to get the new javac to link correctly. 


---

### Post by Miles_Prower on 2012-07-30
[http://xkcd.com/979/](http://xkcd.com/979/)

The problem ended up being this: 
The java installation included in ubuntu 12.04 puts the java executable here:
/usr/lib/jvm/java-6-openjdk-i386/bin/java
if you open the robocode launcher with vim 
```
 sam@samathome:~$ sudo vim /usr/games/robocode 
```
we see on line 21 that the game expects the JRE to reside in 
/usr/lib/jvm/java-6-openjdk/bin/java

so if you are having this problem, what you need to do is this:
- open /usr/games/robocode in whatever text editor (will need root permissions)
- replace "java-6-openjdk" with "java-6-openjdk-i386" on line 21
- save, quit, launch robocode.

Note that if you're using a different cpu architecture than i386, the java executable will be in another folder. i386 is the default though, so most installs will use that.

I've logged a bug on the robocode project [here]("https://sourceforge.net/tracker/?func=detail&aid=3552331&group_id=37202&atid=419486")

---

