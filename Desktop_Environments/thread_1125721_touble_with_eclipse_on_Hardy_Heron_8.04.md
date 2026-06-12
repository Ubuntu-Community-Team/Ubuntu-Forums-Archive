---
title: "touble with eclipse on Hardy Heron 8.04"
date: 2009-04-14
forum: Desktop Environments
---

### Post by mzeal on 2009-04-14
I am trying to get eclipse running with Sun jdk.
I followed directions i've found on this forum:
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
e.g. 
sudo apt-get install eclipse sun-java6-jdk
sudo update-java-alternatives -s java-6-sun 
sudo -b gedit /etc/jvm
etc
Now my default java rt comes as following
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

The problem is, when I call eclipse, it pops empty dialog box after asking for working folder. Running eclipse with -clean or -debug options doesn't help either... Can someone advise me, is there something from gtk i have to install ?

i am running eclipse 3.4 CDT from my home folder ( just uncompressed it there), because i have to use it for Qt Eclipse integration...Would it be possible to upgrade repository version 3.2 to 3.4? That would also solve my dilemma.
Thanks,
-V

---

