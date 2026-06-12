---
title: "Unpacking Open Office 3 in 8.10"
date: 2009-03-25
forum: General Help
---

### Post by Famished on 2009-03-25
I have Open Office 3 on Windows XP.  I have just started with Linux and unpacked 000300_m15_native....and tried to install it with sudo to get the java.   I thought I'd succeeded but, right at the end of the 'install' it crashed.   Here's what  I did[INDENT][I]Running installer
/var/tmp/install_6005/usr/java/jre1.6.0_11/bin/java -DHOME=/home/bertram -DJRE_FILE=jre-6u11-linux-i586.rpm -jar JavaSetup.jar
System locale: en_US
Root privileges
OS: Linux
Mode: installation
Path to packages: /home/bertram/OOO300_m15_native_packed-1_en-US.9379/RPMS/
Jar file: /home/bertram/OOO300_m15_native_packed-1_en-US.9379/JavaSetup.jar

[/I][/INDENT]And here's the 'fail' detail
[LEFT]__________________________________
[/LEFT]
[INDENT][I]error: Failed dependencies: ooobasis3.0-core04 is needed by openoffice.org3-dict-fr-3.0.1-9379.i586 openoffice.org3 is needed by openoffice.org3-dict-fr-3.0.1-9379.i586 /bin/sh is needed by openoffice.org3-dict-fr-3.0.1-9379.i586

[/I][/INDENT]How do I get hold of these dependences 

(very much a newbie, I'm afraid)

---

### Post by kanikilu on 2009-03-25
If you can't wait for the next version of Ubuntu to get OO.o3, I would suggest installing it from the PPA, rather than manually:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Here's a general [PPA Overview](https://help.launchpad.net/Packaging/PPA), if you're interested.

---

### Post by Thelasko on 2009-03-25
Linux doesn't work like Windows, you can't just install the newest release of a program and expect it to work.  The programs on a Linux system are interdependent with one another, this is both a strength and a weakness.

This is also why Ubuntu has a new [release]("http://www.ubuntu.com/products/whatIsubuntu/releases") every six months.  If you can't wait until next month for the newest release, I suggest you use the PPA like kanikilu suggested.

For more information about installing software in Ubuntu, [please read this page.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by ubersolid on 2009-03-25
This here is a good guide for setting up openoffice 3 in ibex, with the ppa.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by abn91c on 2009-03-25
> **ubersolid said:**
> This here is a good guide for setting up openoffice 3 in ibex, with the ppa.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
this is the best guide around, before you try it, the OP will need to undo what he did previously, to install JAVA do ```
sudo apt-get install ubuntu-restricted-extras
```

---

