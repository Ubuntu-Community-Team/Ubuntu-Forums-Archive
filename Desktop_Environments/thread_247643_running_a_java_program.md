---
title: "running a java program"
date: 2006-08-30
forum: Desktop Environments
---

### Post by seedsgrow on 2006-08-30
When I try to run a java program by entering the java -jar command in a terminal, I get the message "JVM not found: libjvm.so - libjvm.so" despite having j2sdk installed and having run ldconfig after installing it. What do I need to do to run a stand alone Java program?

---

### Post by hajk on 2006-08-31
You have to make j2sdk the default version, there is a HOWTO in the wiki.

---

### Post by seedsgrow on 2006-08-31
I have read and followed the suggestions in the wiki. I ran the "update-alternatives --config java" and "update-alternatives --config jar" commands and set the version of j2sdk I installed as default. I also ran the command to set a javac preference, but the j2sdk was the only Java version that provided support for that. That was all before I tried to run the Java program using the "java -jar [file.jar]" command. The program can't find the jvm.so file for some reason.

---

### Post by hajk on 2006-08-31
Now I have the same problem too...

There's something strange going on with /etc/alternatives -- I have on one machine at one time installed j2sdk 5.0 from Sun (using the deb-packaging routine), then removed it and replaced it by the Blackdown 1.4 version in the repositories. So, there is now a single version of javac installed, but the link in /etc/alternatives is still pointing to the non-existing (Sun) version, /usr/bin/javac is a symlink to /etc/alternatives, and update-alternatives won't update because there is nothing to choose... 

I just installed the Blackdown version on my laptop (a recent fresh install of Dapper), and there the symlinks are all correct.

I don't know how to solve the alternatives problem... I notice that there is some sort of database in /var/lib/dpkg/alternatives, could that be used? Or remove/change all those pesky symlinks by hand? Alternatively, do a fresh install of Edgy when it releases in a few months, and work on my laptop instead.:confused:

---

### Post by JackDog on 2006-09-08
The best option that I have found is to bypass ubuntu entirely for java. Just download j5 from sun, unpack it in opt and set your paths in /etc/profile to point to it. 

I have been using ubuntu for 2 years as a professional java developer and have never had synaptic/ubuntu properly manage my java installs.

---

### Post by seedsgrow on 2006-09-17
The best option that I have found is to bypass ubuntu entirely for java. Just download j5 from sun, unpack it in opt and set your paths in /etc/profile to point to it.

I have been using ubuntu for 2 years as a professional java developer and have never had synaptic/ubuntu properly manage my java installs.


Thanks for the idea. It will have to be IBM Java for me, I think, because I am running a PowerPC machine (a Mac mini with a G4 processor). I have their J2SDK 1.5 installed, although I went through the trouble of making an apt package and installing it through Synaptic with the idea I could get upgrades automatically that way. It works to open web-based Java programs in Konqueror, although not in Firefox. When something like this doesn't work quite right, I wonder if it is Ubuntu or my having ppc architecture that is responsible. In this case, it could be the program I am trying to run that is not adapted to my system.

---

