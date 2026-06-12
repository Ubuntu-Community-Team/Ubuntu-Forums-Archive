---
title: "How could I install jdk without apt-get?"
date: 2011-05-24
forum: Desktop Environments
---

### Post by saidbakr on 2011-05-24
Hi,
I have jdk-6u21-linux-i586.bin. I tried to install it into Ubuntu for running netbeans ide. However, the netbeans installer does not able to find the Java and I have to supply it with javahome directive to install it. In addition, Ubuntu seems to be does not able to feel with the jdk installation, any package that need java and its installation using *.deb alert that it needs somethings among of them jdk.

I would like to know how to install jdk from my bin file, because the downloading from apt-get is not a suitable option for me due to very slow Internet connection.

---

### Post by wwlliiuu2009 on 2011-05-25
You can have a look at [this]("http://168.site90.net/doku.php?id=ubuntu-download-and-install-jdk-bin").

---

### Post by saidbakr on 2011-05-26
Hi,
Thank you very-much for trying helping me. However, your solution regarded in your reply which is inked to [this link]("http://168.site90.net/doku.php?id=ubuntu-download-and-install-jdk-bin") does not offer a complete task requirements that i look for it. For example, installing Debian package that includes Java software, require or missing java-jdk by the system, and the os require to install or download it again which looks like that Ubuntu does not detect the our manual installation of jdk.

---

### Post by 1885 on 2011-05-26
> **saidbakr said:**
> Hi,
I have jdk-6u21-linux-i586.bin. I tried to install it into Ubuntu for running netbeans ide. However, the netbeans installer does not able to find the Java and I have to supply it with javahome directive to install it. In addition, Ubuntu seems to be does not able to feel with the jdk installation, any package that need java and its installation using *.deb alert that it needs somethings among of them jdk.

I would like to know how to install jdk from my bin file, because the downloading from apt-get is not a suitable option for me due to very slow Internet connection.

I installed the bin file from sun years ago on Ubuntu.  Then you set the class path in bash.
If you are doing this for profit read the license. 

I put Java in /opt/ these days.  I will install Java on a server at work(Edcuation) and I'll get back with you after I set the classpath.  My install will be 32 bit.  I'll also try it on wubi. 64 bit.

set permission from su.  $sudu -i
#chmod 755 [jdk-6u25-linux-i586.bin]("http://download.oracle.com/otn-pub/java/jdk/6u25-b06/jdk-6u25-linux-i586.bin")
then
#./[jdk-6u25-linux-i586.bin]("http://download.oracle.com/otn-pub/java/jdk/6u25-b06/jdk-6u25-linux-i586.bin")

Then set class palth.
[http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html)


Tomcat and netbeans are all separate now.
I run java on a gentoo server so it's a lot different.

---

### Post by saidbakr on 2011-05-27
Thank you, but my problem is not in running java, I already can compile java in terminal, my problem is that any app or package through apt-get that needs java, the apt-get tells me that I have to download jdk again through the apt-get. The question is how could I add the jdk that I have manually installed it, to the Ubuntu package list, so apt-get will not ask again for download it?

---

