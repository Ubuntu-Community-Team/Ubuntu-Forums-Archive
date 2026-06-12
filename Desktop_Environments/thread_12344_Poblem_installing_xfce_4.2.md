---
title: "Poblem installing xfce 4.2"
date: 2005-01-23
forum: Desktop Environments
---

### Post by jozmak on 2005-01-23
Hi, 

I try to install xfce 4.2 on Warty but the installer cannot find the “Postscript converter a2ps” file. I have a file with a similar name “a2p” installed but the installer doesn't seem to recognize it. I don't even know that this is the same file that the installer looking for or something else. 
The Postscript converter is not mentioned in the dependency list in the xfce installation document and i couldn't locate it with synaptic either; so i don't know how proceed from here.
Any suggestion? 

thanks
jozsefmak

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=jozmak]Hi, 

I try to install xfce 4.2 on Warty but the installer cannot find the “Postscript converter a2ps” file. I have a file with a similar name “a2p” installed but the installer doesn't seem to recognize it. I don't even know that this is the same file that the installer looking for or something else. 
The Postscript converter is not mentioned in the dependency list in the xfce installation document and i couldn't locate it with synaptic either; so i don't know how proceed from here.
Any suggestion? 

thanks
jozsefmak[/QUOTE]


Use XFCE's debian Repository to install XFCE easy way- dependecies resolved.

[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

I've used it. Its works very well.

---

### Post by garretwp on 2005-01-24
I am having issues as well. I did not have any issues installing XFCE in hoary but i switched back to warty and when i go to install through apt-get, i get a dependency issue, saying that libgtkhtml2 needs to be installed for xfce-util. But when i go to check to see if libgtkhtml is install, apt-get already states that it is installed. When i go to try to install with the installer i get some kind off error which i cant figure out what it is complaining about. can someone help me get XFCE installed with apt-get and figure out why libgtkhtml is installed but complaining that it is not. I tried reinstalling it but no success.

Garrett

---

