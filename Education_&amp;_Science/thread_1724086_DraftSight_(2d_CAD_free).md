---
title: "DraftSight (2d CAD free)"
date: 2011-04-07
forum: Education &amp; Science
---

### Post by wobert on 2011-04-07
Has anyone installed DraftSight?  

I would like to know how can I install it, it is great to have a 2d CAD for ubunut! it is great that dassault final makes it...

Here the link to the site , hopefully someone can help me.

[http://www.3ds.com/products/draftsight/download-draftsight/#xtor=EREC-509-](http://www.3ds.com/products/draftsight/download-draftsight/#xtor=EREC-509-)[eng-tips-cadforums]-20110406

---

### Post by cwarner7_11 on 2011-04-23
I had trouble installing DraftSight on my 64-bit machine, and these are the instructions I received from Dassault technical services:

DraftSight Linux Beta 32 bit is not supported yet on Linux 64 bit architecture. You can install the x86 installer under x64 but this may causes problems on 64 bit Linux OS. So, it is recommended to install and run DraftSight on 32 bit Linux OS.
A user reported the similar type of error "wrong architecture” on DraftSight community ([https://swym.3ds.com/#community:70/iquestions:2698](https://swym.3ds.com/#community:70/iquestions:2698)). A workaround would be to try installation via Terminal. 

To install the downloaded package DraftSight.deb on Ubuntu x64 using the workaround do following:

1. Open a Terminal window and run 4 commands one by one to install 4 libraries :

sudo apt-get install ia32-libs 
sudo apt-get install libdirectfb-extra 
sudo apt-get install libxcb-render-util0 
sudo apt-get install libaudio2 

2.  In the Terminal window run command to go to the folder where DraftSight.deb package is placed (e.g. Downloads):

cd Downloads

3. In Terminal window run command to force install DraftSight:

sudo dpkg -i --force-architecture DraftSight.deb 

Also, for more information on Premium version of DraftSight, you can send an email to [email]Premium@draftsight.com[/email]
Once again thank you for using DraftSight.

Regards, 
Ravi Ranglani 
DraftSight Technical Support Team 

No problems installing DraftSight on my Ubuntu 10.04 64-bit system with these instructions...

---

### Post by jagwinn on 2011-04-25
Hello,
I just installed DraftSight. I am very happy to say that most of the commands I learned for Autodesk AutoCAD are the same in DraftSight.
This is a good thing for me, because I want to move away from Windows altogether, and AutoCAD was one of the legacy softwares that kept WinXP on my machine.

Again, I am well satisfied with the installed program...but the pdf I downloaded did not fully resolve ( it appears to be written in font that is the same color as the background. The 'bullets' are visible, but the text is not there).

---

### Post by billiard on 2011-04-25
I did the steps in [cwarner7_11]("http://ubuntuforums.org/member.php?u=800260") post from information I found on another site and it did not work for me on Ubuntu 11.04 Beta 2 64 bit OS Natty Narwhal. It showed in the terminal what I posted in this thread I created: [http://ubuntuforums.org/showthread.php?t=1736987&highlight=draftsight](http://ubuntuforums.org/showthread.php?t=1736987&highlight=draftsight) but it appears others are having problems with 64 bit OS too: [http://ubuntuforums.org/showthread.php?t=1706085&highlight=draftsight](http://ubuntuforums.org/showthread.php?t=1706085&highlight=draftsight)

My only work around is that I dual boot into windows if I need to use a program like this that Linux doesn't support.

For anyone that uses DraftSight to edit or make a DWG and then open it with AutoCAD there will be a warning displayed that says it is foreign drawing in AutoCAD. It doesn't appear to be a problem just stating that it was either not created or edited by AutoCAD. The warning can be turned off. Just letting anyone know.

---

### Post by 71GA on 2012-01-30
How can i run draftsight from terminal???

---

### Post by Gemnoc on 2012-02-09
Look into the DraftSight launcher properties, and copy the command field into the terminal. If it's not changed from the version from 6 months ago, it should be

```
/opt/dassault-systemes/draftsight/bin/DraftSight
```

---

### Post by 71GA on 2012-02-10
Thank you :) SOLVED

---

### Post by wobert on 2012-12-01
Hello Ravi Ranglani ,

Are the commands you shared me still the same needed? Is it now supporting 64 bit systems?  

Thanks for your help

---

### Post by Bandit on 2012-12-07
Kinda late to the thread. But I have used Draftsight many times before. Before I retired I was an Engineer/Draftsman using Solidworks. Sadly SW isnt available for Linux or even OSX..

---

### Post by Morozov on 2012-12-27
Does eny one experience this problem on 64 bit machine;
alex@alex-Studio-XPS-1340:~/Downloads$ sudo dpkg -i --force-architecture draftSight.deb
dpkg: regarding draftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libdirectfb-extra (>= 1.2.7-2)
dpkg: error processing draftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 draftSight.deb

---

### Post by dbflyrod on 2013-05-13
> **Morozov said:**
> Does eny one experience this problem on 64 bit machine;
alex@alex-Studio-XPS-1340:~/Downloads$ sudo dpkg -i --force-architecture draftSight.deb
dpkg: regarding draftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libdirectfb-extra (>= 1.2.7-2)
dpkg: error processing draftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 draftSight.deb

THis reply is very late but I've have the same problems with 12.04 on 32 bit. I finally ran into a fix just before I found this one. here is a link. Hope it helps you as well. [http://linuxaideddesign.blogspot.com/2012/03/draftsight-and-ubuntu-1204-lts-64bit.html](http://linuxaideddesign.blogspot.com/2012/03/draftsight-and-ubuntu-1204-lts-64bit.html) I actually had to do steps 3-7 twice with two different deletes due to 2 dependency issues. Only did this this morning but everything seems to be working well. Good luck
DB

---

