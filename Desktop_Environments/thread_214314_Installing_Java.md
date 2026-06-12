---
title: "Installing Java"
date: 2006-07-12
forum: Desktop Environments
---

### Post by 3dgamer on 2006-07-12
Hi ...
Please i want to tell how to install java runtime on my machine ... and where to download the .bin file ...

---

### Post by aysiu on 2006-07-12
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by philippe_carlo on 2006-07-12
You may want to take a look at easy ubuntu:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by 3dgamer on 2006-07-12
Hi philippe_carlo
when i run    tar -zxf easyubuntu-3.021.tar.gz
i got an error message what to do ?

---

### Post by jordilin on 2006-07-12
The easiest way, follow the next steps:
To install the java vm from Sun, download the package jdk-1_5_0_05-linux-i586.bin and do the following:
$sudo apt-get install java-package fakeroot
$fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin
$sudo dpkg -i sun-j2sdk1.5_1.5.0+update05_i386.deb

Then, you must tell ubuntu to use this java version by doing:
(Breezy uses gij by default)
$sudo update-alternatives --config java

Obviously substitute jdk-1_5_0_05-linux-i586.bin by the most actual version of java from java.sun.com

---

### Post by 3dgamer on 2006-07-12
ok i manually untar it .. i will see what will happen next

---

### Post by timppa_m on 2006-07-12
install Automatix. With it installing is peace of a cake!
[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)  8)

---

### Post by philippe_carlo on 2006-07-12
What error message? Make sure to wait for the entire package to download first and to have write permissions in the directory where you unpack.

---

