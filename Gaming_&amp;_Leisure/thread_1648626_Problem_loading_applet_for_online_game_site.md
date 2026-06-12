---
title: "Problem loading applet for online game site"
date: 2010-12-19
forum: Gaming &amp; Leisure
---

### Post by dfletch1971 on 2010-12-19
Hello,
Thanks in advance for all assistance offered. I am a ubuntu neophyte. Old dog slowly learning a new trick. 
When I was with windows, I played an online cribbage game with ecribbage.com. Now with ubuntu 10, the game applet no longer loads. I have tried trouble shooting java, installing latest version. The applet for yahoo cribbage loads with no problem. The site admin for ecribbage is willing to try remote access to my computer but I was hoping someone here could help me fix it first. Or tell me if it is just not going to work.
Please understand that this is all very new, thanks for your patience. Hey, I can open my terminal now! That is progress
Diana

---

### Post by lykeion on 2010-12-19
Personally I'd never let a web site have remote control access to my computer.

To help you some info is needed:
* Your Ubuntu version
* Currently installed java browser plugin (check add-ons in the menu)

Some web sites may have problems with IcedTea java plugin, so installing Sun Java plugin might be a solution.

In Lucid/Maverick you need to enable Partner repository to install Sun Java plugin. In earlier versions it's in the Multiverse repositories. 
Read [Ubuntu Documentation/Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") to see how you enable repositories in Ubuntu.

After enabling the right repository you can launch a package manager (Ubuntu Software Center or Synaptic), 
search for "java plugin" and remove IcedTea Java Plugin and install Sun Java 6.0 Plugin. 
Then restart your browser and test the page again.

---

### Post by dfletch1971 on 2010-12-19
I am using ubuntu 10.10 the latest I believe. I just updated, however I had the same problem with the earlier version. 
I looked at the software center. It listed iced tea. So I followed the instructions on partner repositories. Then selected sun java. It has version 6 listed. Also there are about  2 dozen additional files that are attributed to sun java. Do I need all of these as well?  I restarted firefox, no luck.  I have tried chrome and epiphany as well. 
Anything I am missing?
Thanks

---

### Post by lykeion on 2010-12-20
Ok, I tested the ecribbage site and I couldn't reproduce any problems with loading the java applet. You can try this, it should remove and install the packages you need.

1. Start a terminal (Applications > Accessories > Terminal)
2. Refresh the repositories with this command:
```
sudo apt-get update
```
3. Remove all OpenJDK packages with this command:
```
sudo apt-get remove icedtea6-plugin icedtea-6-jre-cacao openjdk-6-dbg openjdk-6-demo openjdk-6-doc openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-jre-zero openjdk-6-source
```
4. Install Sun Java JRE and browser plugin with this command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
5. Restart browser and try again.

---

### Post by Cousjava on 2010-12-20
This is very similar to the problem which a lot of people have been having with Minecraft, which has been talked about on several other threads on this site, another Java-based game. I've just gone and tested another couple of Java-based games, i.e. Runescape, and they don't seem to be working either. So I definitely think there is something wrong with Java on Ubuntu Maverick.

---

### Post by dfletch1971 on 2010-12-22
Huzzah!   Thank you Lykeion!  I followed your instructions and it worked.  You have totally made my day.

---

