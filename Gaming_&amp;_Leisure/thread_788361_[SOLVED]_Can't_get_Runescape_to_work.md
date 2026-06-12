---
title: "[SOLVED] Can't get Runescape to work"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by jose158 on 2008-05-09
I keep getting this every time I try to do high detail in Runescape. To play I have to go to Unassigned Java Applet, but it loads slower and I don't get all the sound effects. Help?:confused:

---

### Post by scragar on 2008-05-09
that's a bit of a firefox bug, basicly it's banning access for any java program to read and write files to a cache dir on your HD as part of a security measuer(after it was found that attempting to read or write to files using .. to get out of cache dir was dangerous).

I use konqueror as a lightwieght and suitable match, however I suspect that once JAVA fix the problem on their end firefox will stop being so extreme with the security. :P

---

### Post by jose158 on 2008-05-09
> **scragar said:**
> that's a bit of a firefox bug, basicly it's banning access for any java program to read and write files to a cache dir on your HD as part of a security measuer(after it was found that attempting to read or write to files using .. to get out of cache dir was dangerous).

I use konqueror as a lightwieght and suitable match, however I suspect that once JAVA fix the problem on their end firefox will stop being so extreme with the security. :P
Well, I installed Konqueror but I still can't play it. :(

---

### Post by doorknob60 on 2008-05-10
I get that problem when I use the Icedtea Java plugin. do the following commands:
```
sudo apt-get install sun-java6-plugin
sudo update-java-alternatives -s java-6-sun
```

Then it should work fine (I'm playing RUnescape right now, feel free to add me, doorknob60 is my RSN :)

---

### Post by jose158 on 2008-05-10
> **doorknob60 said:**
> I get that problem when I use the Icedtea Java plugin. do the following commands:
```
sudo apt-get install sun-java6-plugin
sudo update-java-alternatives -s java-6-sun
```Then it should work fine (I'm playing RUnescape right now, feel free to add me, doorknob60 is my RSN :)
Well, I tried what you said and got this:```
jose@jose-desktop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for jose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jose@jose-desktop:~$ sudo update-java-alternatives -s java-6-sun
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for jhat.
No alternatives for jrunscript.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for schemagen.
No alternatives for wsgen.
No alternatives for wsimport.
No alternatives for xjc.
No alternatives for xulrunner-addons-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
No alternatives for xulrunner-addons-javaplugin.so.
jose@jose-desktop:~$ 

```

---

### Post by jose158 on 2008-05-12
I miss Runescape:(

---

### Post by SoloSalsa on 2008-05-12
I've never had *anything*-Java work in Ubuntu.

---

### Post by ethoxyethaan on 2008-05-13
i have to confirm i had the same problem in the 64 bit version on buntu 7.10

to solve it i just installed the 32 bit version.

---

### Post by scragar on 2008-05-13
```
sudo apt-get install sun-java6-plugin
```

[http://ubuntuforums.org/showthread.php?t=26250](http://ubuntuforums.org/showthread.php?t=26250) <-- see second post to set up java in konqueror, java needs a similar path to be entered in a similar way.

---

### Post by jose158 on 2008-05-16
I really want to play runescape again, specially since the new graphic changes are coming in a couple of months:(

---

### Post by jose158 on 2008-05-16
NVM I finally got it!!:guitar:

---

### Post by doorknob60 on 2008-05-16
Whats your runescape username, I'll add you :D Can't wait for the graphics update, I hope it doesn't mess up in ubuntu (it randomly freezes right now, it sucks).

---

### Post by jose158 on 2008-05-18
> **doorknob60 said:**
> Whats your runescape username, I'll add you :D Can't wait for the graphics update, I hope it doesn't mess up in ubuntu (it randomly freezes right now, it sucks).
It's Jose_link1. And yes I can't wait for the graphics update either:popcorn:

---

