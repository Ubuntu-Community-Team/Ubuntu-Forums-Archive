---
title: "Stubborn Java Installation"
date: 2011-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dr.FrankenStein_ on 2011-02-02
Hey Everyone.. having alot of issues with jre-6u23-linux-i586.bin and jre-6u23-linux-i586-rpm.bin.!! Neither is going the way it should and I've followed the instructions flawlessly for both types of pkgs from java.com,- plus alot of other links. I've tried it 7 ways to sunday-=> considering i'm currently having alot of java jre jdk jvm JAVA! problems,.. everything i do (alien) runs into dependency problms. Am I also having permission errors?? sounds like it {i'm using and  Dell Dimension 8200 series, Linux Mint 10.10 [meerkat] fresh install} someone please help and put an end to   my misery.:( Thanx In Advance

---

### Post by Dr.FrankenStein_ on 2011-02-02
Also i should add intalling sun-java6-jre via apt-get/aptitude/synaptic [.deb] i get a long output of java dependency errors..which leads me to the option of rpm..tried to convert to deb with alien and it wants to use java-- Javas not working :( i'm lost  AnyBody?     output is very long and hectic

---

### Post by John.Rayfield on 2011-02-02
Ok, as a start, what is the very first error msg, or warning that you get during installation ?

---

### Post by Dr.FrankenStein_ on 2011-02-02
Hi.. I hope your ready lol  ok 
[www.linuxquestions.org/questions/linux-newbie-8/stubborn-java-installation-860143/]("http://www.linuxquestions.org/questions/linux-newbie-8/stubborn-java-installation-860143/")

---

### Post by Dr.FrankenStein_ on 2011-02-02
Actually sorry you may not be a member and in that case you might have a big white box over the thread... 

sudo aptitude install sun-java6-jre
The following partially installed packages will be configured:
  sun-java6-demo sun-java6-jdk sun-java6-plugin sun-java6-source 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up sun-java6-jdk (6.22-0ubuntu1~10.10) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/bin/HtmlConverter doesn't exist.
dpkg: error processing sun-java6-jdk (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-demo:
 sun-java6-demo depends on sun-java6-jdk (>= 6.22-0ubuntu1~10.10); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-demo (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-plugin (6.22-0ubuntu1~10.10) ...
No apport report written because MaxReports is reached already
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so doesn't exist.
dpkg: error processing sun-java6-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-source:
 sun-java6-source depends on sun-java6-jdk (>= 6.22-0ubuntu1~10.10); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-source (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 sun-java6-jdk
 sun-java6-demo
 sun-java6-plugin
 sun-java6-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-jdk (6.22-0ubuntu1~10.10) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/bin/HtmlConverter doesn't exist.
dpkg: error processing sun-java6-jdk (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-source:
 sun-java6-source depends on sun-java6-jdk (>= 6.22-0ubuntu1~10.10); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-source (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-plugin (6.22-0ubuntu1~10.10) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so doesn't exist.
dpkg: error processing sun-java6-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-demo:
 sun-java6-demo depends on sun-java6-jdk (>= 6.22-0ubuntu1~10.10); however:
  Package sun-java6-jdk is not configured yet.
dpkg: error processing sun-java6-demo (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jdk
 sun-java6-source
 sun-java6-plugin
 sun-java6-demo

---

### Post by lykeion on 2011-02-02
As the error output says, you have some packages that were not installed properly.

Try to start Synaptic and fix these:
**Synaptic > Edit > Fix broken packages**

If that doesn't work try to remove the partially installed packages: 
**sun-java6-demo sun-java6-jdk sun-java6-plugin sun-java6-source**

Then you can try to install **sun-java6-jre**

Also it makes me wonder why you tried to install the jdk. This is only needed if you are going to do Java development. 
If you simply want to play minecraft or whatever the jre is enough.
And if you need the Java browser plugin for web sites like pogo, you should install **sun-java6-plugin**

---

### Post by Dr.FrankenStein_ on 2011-02-02
ok ive tried all that several times even my using the more advanced command [aptitude -f] I'm sure I'll get back to you  thank you

---

### Post by Dr.FrankenStein_ on 2011-02-02
!:):) Thanks lykeion =>it made a liar out of me, computers seem to do that a lot. Oddly there wasnt any broken packages, which in my eyes there were cause 3 partially installed packages that dont work are broken to me right? So I closed everything tried to remove it ALL again. Rebooted and reinstalled again its seems to have finally done the trick, and now vuze, FROSTWIRE!! works fine and Java finally shows up in about : plugins! If it just wouldv'e done this 2 days ago... Whatever was conflicting its fixed now

---

