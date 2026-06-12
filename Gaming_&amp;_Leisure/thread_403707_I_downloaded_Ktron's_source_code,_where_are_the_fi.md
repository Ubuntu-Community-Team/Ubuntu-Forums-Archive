---
title: "I downloaded Ktron's source code, where are the files?"
date: 2007-04-07
forum: Gaming &amp; Leisure
---

### Post by Slipmyknot101 on 2007-04-07
Hello,

I am a semi beginner to Ubuntu as I have a question about where Ktron's source code is located in my filesystem. 

I read up on Ktron last night and I discovered that the source code for Ktron is in Kdegames package. I downloaded that, however, I don't know where to find specifically Ktron's source code. 

I'm trying to load it into kdbg so that I can see how a game as simple as Ktron is programmed. This is because I am an aspiring future programmer.

If someone could help, that would be great.


Trevor.

---

### Post by nzjethro on 2011-05-26
install subversion AKA svn using:

sudo apt-get install svn

then open a terminal and type:

svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdegames/ktron/

then, the code should be in your home folder (/home/user/)

Code from [http://www.kde.org/applications/games/ktron/development](http://www.kde.org/applications/games/ktron/development)

---

