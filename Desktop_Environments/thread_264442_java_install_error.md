---
title: "java install error"
date: 2006-09-24
forum: Desktop Environments
---

### Post by itchanddino on 2006-09-24
I get this error whenever I try to install java through easyubuntu, automatix or just the repos. I did a fresh install of Xubuntu between each attempt to install java. Any help would be awesome.

Setting up sun-java5-bin (1.5.0-06-1)...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up sun-java5-bin (1.5.0-06-1)...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin

---

### Post by Dinerty on 2006-09-24
Install the latest java by:

**Originally created by **Artifical Intelligence**

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick Linux self-extracting file. Download it to your Desktop.

```

cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java

```

When asking for which version you want to choose pick;

```

3        /usr/lib/j2sdk1.5-sun/bin/java

```

Testing;

```

java -version

```

Making a Launcher for Java Control Center;

```

sudo gedit /usr/share/applications/java.desktop

```

fill in;

```

[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by itchanddino on 2006-09-24
sudo update-alternatives --config java

when I put that in, it says 

There is only 1 program which provides java
(/usr/lib/j2re1.5-sun/bin/java). Nothing to configure

then it goes back to a prompt.

java -version returns

Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment

---

### Post by itchanddino on 2006-09-25
I just tried again, got the same set of errors :( Is there anything else I should try?

---

### Post by Dinerty on 2006-09-25
Did you copy and paste the commands?

---

### Post by itchanddino on 2006-09-25
Yes, exactly. I triple checked.
I'm using Xubuntu if that makes a difference.

---

### Post by Dinerty on 2006-09-25
What happens when you type:

```
locate libjava.so
```

---

### Post by fuzzybr80 on 2008-01-16
I had the same issue. The problem with mine was that the shortcut /usr/bin/java was created as a hard link to my actual java (in /usr/java/latest/bin/java). I deleted /usr/bin/java and created it as a soft/symbolic link instead:

rm /usr/bin/java
ln /usr/java/latest/bin/java /usr/bin/java -s

and it works subsequently.

---

### Post by fuzzybr80 on 2008-01-16
I should say the previous post refers to the problem about Java 1.5.0: running java -version gives:

Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment

and not the original poster's issue.

---

### Post by kvdbreem on 2008-02-26
Followed Fuzzybr80's advice and got it working.  Didn't need to create packages or anyting.  Usually I just run the bin installer in a path like /usr/local and link from there.  The softlink command suggested seems to work.  

What makes me wonder about this problem is the fact that going into <java install path>/bin and typing ./java lets you run java no problem.

---

