---
title: "how to install java runtime environment 1.4.2"
date: 2006-02-25
forum: Desktop Environments
---

### Post by linows3 on 2006-02-25
Hi everybody:
New to Ubuntu Linux, I tried SuSE 9.3 for almost a year but had so many problems with it that decided to give Ubuntu 5.10 a try.
This is what I've done so far;
a) downloaded jre 1.4.2 in bin format:) 
b) want to install it but don't know where and how to self-extract it.:confused: 

Any help will be greatly appreciated. Thanks:)

---

### Post by Xian on 2006-02-25
If you install the [J2RE-1.4](http://packages.ubuntu.com/breezy/devel/j2re1.4) package it will place java on your system and make all the needed configurations.

---

### Post by Trab on 2006-02-25
two OTHER options for getting java to work (i prefer both of these... i manually set up java once, and it pissed me off...)
automatix will do this for you (search the site for automatix)
or check synaptic for blackhawk java...
i just found doing it by myself was long, and didnt work often...

---

### Post by curley_sue on 2006-02-25
I've discovered this (*) only after installing Java manually (**) following the instructions found under help -> ubuntu starter guide -> applications -> java (which I also attached)

**BUT: I guess this is the easy way** - (*)
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)


(**)
Java

1.&#8195;

How do I install the J2SE Runtime Environment (JRE) 5 (1.5) with Firefox plugin?

       1.

          Make sure the multiverse repository is enabled. (See How do I add Universe and Multiverse?)
       2.

          Go to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and click on &#8220;Download JRE 5.0 Update 4&#8221;. Ensure you do not choose the link with the NetBeans bundle.

          At the time of this writing J2SE is at version 5.0 Update 4. This is subject to change. If you do not see this version on Sun's website, download the newest version displayed.
       3.

          You must first accept the licence, then click on &#8220;Linux self-extracting file&#8221; (jre-1_5_0_04-linux-i586.bin). Save this file to your hard drive.
       4.

          Install the java-package package with Synaptic (See How do I use Synaptic to install packages?)

          Miscellaneous - Text Based (multiverse) > java-package
       5.

          Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x jre-1_5_0_04-linux-i586.bin

       6.

          To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

       7.

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

---

### Post by Ramses de Norre on 2006-02-25
I'd suggest [http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754) to install java, it's a newer version.
Just follow the how-to but change the ...-05 in the version number to ...-06 (that's the version you'll download), be careful to do it everywhere, it wont work otherwise!
And in the reconfigure section: you'll probably need to choose the last option (check the version numbers).

---

### Post by clemcat on 2006-02-25
I can play my Washington Post Crossowrds now, thanks all.

---

