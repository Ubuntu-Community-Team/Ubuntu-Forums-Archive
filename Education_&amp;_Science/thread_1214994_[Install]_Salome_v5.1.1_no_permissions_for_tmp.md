---
title: "[Install] Salome v5.1.1 no permissions for /tmp"
date: 2009-07-16
forum: Education &amp; Science
---

### Post by Merka73 on 2009-07-16
Hello to everybody
I am trying to install salome 5.1.1 on ubuntu 9.04 32bit, so I downloaded the debian etch version of salome from this site:
[http://www.salome-platform.org/download/dl511/]("http://www.salome-platform.org/download/dl511/")
To start the installation procedure, I typed this command in the terminal:
```
merka73@merka73-laptop:~$ sudo /home/merka73/Desktop/InstallWizard_5.1.1_Debian_4.0/./runInstall
[sudo] password for merka73:
```
but I received at step 4/8 the following permissions issueis:
[http://www.filefactory.com/file/ahd6h65/n/Installation_Images_pdf](http://www.filefactory.com/file/ahd6h65/n/Installation_Images_pdf)
Could anyone help me... please... because I don't understand where is the problem.

Thanks in advance
Merka73
PS: Sorry for my english

---

### Post by strollerdude on 2009-07-20
Hi Merka 73,
I've tried the two commands on [http://ubuntuforums.org/showthread.php?p=4613772](http://ubuntuforums.org/showthread.php?p=4613772) which I was directed to by [http://www.salome-platform.org/forum/?groupid=10&forumid=9&thread=2656](http://www.salome-platform.org/forum/?groupid=10&forumid=9&thread=2656)

I don't know how "safe" or correct these commands are, but they get me over that permissions step you are stuck on. 

For any one who might know a more correct way, the commands from the above post are 

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

Salome is installing at the moment. I'll let you know if there are any problems.

---

### Post by strollerdude on 2009-07-22
I also have had to include libgfortran.so.1 from the information on this link. It is needed for meshing.
[https://answers.launchpad.net/ubuntu/+source/gcc-4.1/+question/72388](https://answers.launchpad.net/ubuntu/+source/gcc-4.1/+question/72388)

---

### Post by strollerdude on 2009-07-22
Another easier option is to use the caelinux version 4.1.4 which includes aster for FEA. It doesn't look as nice as version 5.1.1.
It can be found at [http://www.caelinux.com/CMS/index.php?option=com_content&task=view&id=46&Itemid=40](http://www.caelinux.com/CMS/index.php?option=com_content&task=view&id=46&Itemid=40)

---

