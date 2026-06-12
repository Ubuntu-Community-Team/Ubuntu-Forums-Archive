---
title: "Geometry And Algebra with GeoGebra"
date: 2007-10-25
forum: Education &amp; Science
---

### Post by crislosi on 2007-10-25
Hi everyone!! I've found a new program for geometry and algebra, his name is GeoGebra and it looks like Cabri.
The installation in Ubuntu is very easy.
First, install jre1.6

> sudo apt-get install sun-java6.bin sun-java6-demo sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-source

If you are using Gutsy only install ubuntu-restricted-extras:

> sudo apt-get install ubuntu-restricted-extras

After that, download the program in this link
[URL="http://www.geogebra.org/download/InstData/Linux/NoVM/GeoGebra_3_0_0_0_Release_Candidate_1.bin"]
Download GeoGebra[/URL]

Then in a terminal execute the installer with this command:

     > sh ./GeoGebra_3_0_0_0_Release_Candidate_1.bin  

Follow the instructions of the installer and that's all.
You can create a Launcher with Principal Menu

The program is very usefull for the maths teachers and students. With this program you be able draw math' figures, calculates derivatives.... and export your works like png, html, pst etc

You can obtain all information about its use in this [Link]("http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=75&Itemid=61")

here is a screenshot

[[IMG]http://img507.imageshack.us/img507/9475/geogebracm2.th.png[/IMG]](http://img507.imageshack.us/my.php?image=geogebracm2.png)

Well this is my first contribution in Ubuntu Forums, I hope that somebody is very useful this program that I've found by there.

Excuse me for my bad english 

Bye :guitar:

---

### Post by episodic on 2007-10-25
THANKS! This is awesome.








> **crislosi said:**
> Hi everyone!! I've found a new program for geometry and algebra, his name is GeoGebra and it looks like Cabri.
The installation in Ubuntu is very easy.
First, install jre1.6


If you are using Gutsy only install ubuntu-restricted-extras:



After that, download the program in this link
[URL="http://www.geogebra.org/download/InstData/Linux/NoVM/GeoGebra_3_0_0_0_Release_Candidate_1.bin"]
Download GeoGebra[/URL]

Then in a terminal execute the installer with this command:

     

Follow the instructions of the installer and that's all.
You can create a Launcher with Principal Menu

The program is very usefull for the maths teachers and students. With this program you be able draw math' figures, calculates derivatives.... and export your works like png, html, pst etc

You can obtain all information about its use in this [Link]("http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=75&Itemid=61")

here is a screenshot

[[IMG]http://img507.imageshack.us/img507/9475/geogebracm2.th.png[/IMG]](http://img507.imageshack.us/my.php?image=geogebracm2.png)

Well this is my first contribution in Ubuntu Forums, I hope that somebody is very useful this program that I've found by there.

Excuse me for my bad english 

Bye :guitar:

---

### Post by BryanFRitt on 2008-01-19
I'm using the 64bit version of KUbuntu and this doesn't work for me, I get:

sudo apt-get install sun-java6.bin sun-java6-demo sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-source
[sudo] password for bryan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6.bin

removing sun-java6.bin from the list I get:

sudo apt-get install sun-java6-demo sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-demo is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-jdk is already the newest version.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

removing sun-java6-plugin I get:
sudo apt-get install sun-java6-demo sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-demo is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-jdk is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-source is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-alsa libboost-date-time1.34.1 libboost-thread1.34.1
  gstreamer0.10-plugins-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Then trying 
sh ./GeoGebra_3_0_0_0_Release_Candidate_1.bin
I get:
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b531334ee11, pid=13350, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/install.dir.13350/hs_err_pid13350.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by BryanFRitt on 2008-01-20
I downloaded the jar, right click and open with sun java runtime 6, it installed but it took so long if I weren't doing something else, I/most people would have assumed it wasn't working at all.
Now the webstart works, and I'm happy with just a bookmark to that page.
[http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=70&Itemid=57](http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=70&Itemid=57)
Maybe it was restarting my computer after messing with Java install that helped, I don't know.

Geogebra is a great program.

---

### Post by Bubba64 on 2008-01-20
I couldn't get this program unless I used the website download try that just click on the link.

---

