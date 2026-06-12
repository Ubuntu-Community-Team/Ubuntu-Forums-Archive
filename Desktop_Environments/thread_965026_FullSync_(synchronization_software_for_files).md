---
title: "FullSync (synchronization software for files)"
date: 2008-10-31
forum: Desktop Environments
---

### Post by svenskmand on 2008-10-31
Hello everybody,

i was looking for some nice and easy software to synchronize files and i found this thread

[http://ubuntuforums.org/showthread.php?t=327289](http://ubuntuforums.org/showthread.php?t=327289)

then I downloaded FullSync but I can't get it to install, then I was wondering if it where for linux or windows only. I need a cross-platform program with smb and ftp, so FullSync would be perfect.

Anybody have som experience with this program and ubuntu?

Best regards :)

---

### Post by sokolov on 2009-07-04
I've downloaded the .jar-file and it seemed to install fine on my Ubuntu 9.04. No error messages. But how do I start the program now? No entry in the main menu and the console doesn't know fullsync, Fullsync or FullSync. I feel dumb, but how to I launch fullsync after installation?

---

### Post by lchoate on 2009-11-07
I ran in to problems after the installation as well, so here is a little tutorial for FullSync. This is based on: [http://doc.ubuntu-fr.org/fullsync](http://doc.ubuntu-fr.org/fullsync) but for those who speak less french that I do. This corrects the problem **Error: JAVA_HOME is not defined correctly.** The thing is, you may not know you are getting this error because when launched from the icon, nothing happens at all. Anyway lets get it fixed...

If you don't have FullSync yet, download it here: [http://sourceforge.net/projects/fullsync/files/fullsync/](http://sourceforge.net/projects/fullsync/files/fullsync/)

Run the installer as directed. Once installed, you should find the icon under "Internet". If you click it and nothing happens, then here is your fix...

1) To get it to run, open a terminal, type:
```
gedit FullSync/bin/fullsync.sh
```2) Look for the line:
```
#! /bin/sh
```3) Directly below that, type in the following based on your release and jdk:

[CENTER]**JAVA 5**
[/CENTER]
**Dapper** with Java 5 type: JAVA_HOME=/usr/local/java/jre1.5.0_06
**Edgy or Feisty** with Java 5, type: JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

[CENTER]**JAVA 6**
[/CENTER]
**Edgy or Feisty** with java6 type: JAVA_HOME=/usr/lib/jvm/java-6-sun
**Hardy**: JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.14/jre
**Intrepid**: JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.10/jre
**Jaunty**: JAVA_HOME=/usr/lib/jvm/java-6-sun/jre 

[CENTER]**OPEN JDK**
[LEFT]**Intrepid**: JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre
**Jaunty**: JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre 
**Karmic**: JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre[/LEFT]
[/CENTER]

Save the file and restart the program. Should work perfectly now. Good luck.

---

