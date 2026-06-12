---
title: "Repository question"
date: 2005-03-14
forum: Desktop Environments
---

### Post by stryder on 2005-03-14
Hi Peeps 

 im pretty new to Debian so my first choice is Ubuntu , and i must say pretty good choice .. anyway .. is it possible to add [http://ftp.debian.org/debian/pool/main/](http://ftp.debian.org/debian/pool/main/) to the Repository so i can browse the apps ?  also what are the crednetials for the Repository  can it only be certain site, HTTP, FTP , or is it possible to add any site with applications on ?


TIA

Stryder

---

### Post by nemin on 2005-03-14
[QUOTE=stryder]
 im pretty new to Debian so my first choice is Ubuntu , and i must say pretty good choice .. anyway .. is it possible to add [http://ftp.debian.org/debian/pool/main/](http://ftp.debian.org/debian/pool/main/) to the Repository so i can browse the apps ?  also what are the crednetials for the Repository  can it only be certain site, HTTP, FTP , or is it possible to add any site with applications on ?
[/QUOTE]
Yep, that's very well possible. It works exactly the same way as in Debian, because it's not distribution specific but package manager specific (apt, in case of Debian and Ubuntu). You can add repositories to /etc/apt/sources.list. 
See [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html) for more information about apt.
By the way, I don't really recommend you mixing packages from debian and ubuntu.

---

