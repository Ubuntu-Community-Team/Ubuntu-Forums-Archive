---
title: "striving to install java, no luck so far"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Tominator on 2005-12-18
I hope someone can tell what is wrong about the following commands. Thanks in advance, Tom. 
tom@ubuntu:~$ sudo apt-get install fakeroot java-package java-common
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
tom@ubuntu:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.binsudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.debsudo update-alternatives --config java
bash: fakeroot: command not found
tom@ubuntu:~$ java -versionjava version "1.5.0_06"
gij: unrecognized option -- `-versionjava'
Try `gij --help' for more information.
tom@ubuntu:~$ Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
bash: syntax error near unexpected token `TM'
tom@ubuntu:~$ Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

---

### Post by Tominator on 2005-12-18
Then I clicked on the destop icon of the downloaded java and got this,
Could not open the file "/home/tom/Desktop/jre-1_5_0_06-linux-i586.bin"

---

### Post by Tominator on 2005-12-18
gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.

---

### Post by Leif on 2005-12-18
Try this instead : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by Tominator on 2005-12-18
Thanks for trying to help Leif. I have tried your suggestion without good results. Is it possible I am trying to install another java version than the one you are referring to?
tom@ubuntu:~$ sudo apt-get update
Reading package lists... Done
tom@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
tom@ubuntu:~$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
tom@ubuntu:~$

---

### Post by Leif on 2005-12-18
did you use "deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java" ? if that didn't work, try using "deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free" instead and try again

---

### Post by rudiz on 2005-12-18
Look this line got a typo:

tom@ubuntu:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.binsudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.debsudo update-alternatives --config java

after....+update06_i386.deb && sudo update-alternatives--config java


....

---

### Post by rudiz on 2005-12-18
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29)

---

