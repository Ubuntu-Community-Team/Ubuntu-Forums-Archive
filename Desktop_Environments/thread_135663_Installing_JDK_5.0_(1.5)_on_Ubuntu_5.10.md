---
title: "Installing JDK 5.0 (1.5) on Ubuntu 5.10"
date: 2006-02-24
forum: Desktop Environments
---

### Post by SquirrelHavoc on 2006-02-24
Sorry if this has already been asked before, I did some looking, and didn't see anything.

Has anyone got the Linux version of the newest JDK (which is 5.0 or 1.5 I believe) from the java.sun.com website to work on Ubuntu Breezy? I am fairly new to the system configuring of Linux, and I dont know how to set PATH, CLASSPATH, and so on. And the install script seems to just extract files, and doesn't actually set it up for you.

I would just use SPM to install JDK 1.4, but I really need the runtime for 5.0 (1.5) to work with a certain program, but the development part can be any psuedo-recent version.

Anyway, anyone have ideas? Thanks in advance.


P.S. Totally OT, but why do people post threads with subjects like "Read This!!!!11111" so much? It makes it hard to skim through the subjects looking for a certain topic.

---

### Post by nads on 2006-02-24
Use Automatix, it can install both the JDK and JRE automatically for you. Look it up on the forum.

---

### Post by FIONEX on 2006-02-24
This won't be much help but it'll get you on the right track.

Download the bin file from java.sun.com.  Then do $ sudo chmod a+x jdk_1.5.0.bin (or whatever the file name is).  Then to get the installation going, do this $ sudo ./jdk_1.5.0.bin (or whatever the file name is).  Then install the files to somewhere you're going to remember.  Netbeans' location won't be so important but that important part is the JDK's location.  Because after the bin extracts, the location where you saved the JDK is going to have another bin :confused: .  You want to again $ sudo chmod a+x filename.bin and execute it using sudo ./filename.bin .  From there, your java is set up.

You might also have a problem with the gcj because the one distributed with ubuntu is 1.4.2 and obviously you want to be using 1.5.0 to execute new apps like Dr. Java.  So take a look at my thread that I posted yesterday: [http://ubuntuforums.org/showthread.php?t=135328](http://ubuntuforums.org/showthread.php?t=135328) .

If you need anything else, post here and I'll try to get back to you ASAP.  PS.  I hate it when people have threads with the names you mentioned too.

---

### Post by SquirrelHavoc on 2006-02-24
Thank you for your help, I did get it working. It was pretty painless, I always figured there was an easy way of doing it, and hand-editing the config files in /etc was *not* the way to do it :)

---

