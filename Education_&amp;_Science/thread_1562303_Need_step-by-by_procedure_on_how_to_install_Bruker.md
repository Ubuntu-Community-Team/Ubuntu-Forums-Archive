---
title: "Need step-by-by procedure on how to install Bruker Topspin 2.1 on ubuntu"
date: 2010-08-27
forum: Education &amp; Science
---

### Post by jxy007 on 2010-08-27
hello I am new to the ubuntu system. I installed ubuntu to run the bruker topspin software because it does not support the 64-bit windows vista i have now. I have a linux version of Topspin 2.1 with license, but the install.cmd does not run as it just opens up a window of script that is meaningless to me who is not a computer or linux expert. any help is greatly appreciated!

---

### Post by inaho on 2010-09-03
install.cmd it is not the good file (it's for windows, I think)

open a terminal and type the following

sudo -i
cd /media/TOPSPIN_ts21
./install

the programm will install, but then you have to fix the license file 
/usr/local/flexlm/Bruker/licences/license.dat
(information about how to do it are in the mail you should get from Bruker)
 there is actually another problem that I am still trying to fix and that is related to JAVA, as soon as I get soved it I will post the complete step-by-step procedue.

cheers
barbara

---

### Post by inaho on 2010-09-06
hi there, I posted the procedure here:

[http://ubuntuforums.org/showthread.php?p=9813416#post9813416](http://ubuntuforums.org/showthread.php?p=9813416#post9813416)

cheers

---

### Post by hitek on 2010-09-09
[Here]("https://www.bruker-biospin.com/.../How-to-install-the-license070820.pdf") is a link of PDF file explaining the installation method.

---

