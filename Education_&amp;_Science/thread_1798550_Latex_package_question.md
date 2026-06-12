---
title: "Latex package question"
date: 2011-07-06
forum: Education &amp; Science
---

### Post by The__Doctor on 2011-07-06
Hey, I have a a laptop with Windows and Ubuntu on the same machine. On Ubuntu and Windows, I have installed proTeXt (which uses MiKTeX) on Windows and TeX Live on Ubuntu. On the Windows system, I have plenty of space on the partition which it is installed on, so I chose to do a full install, which installs heaps of packages for MiKTeX, but on Ubuntu, I only installed few essential packages, e.g. amsmath. 

I would like to know if there is any way to use the packages I installed on my Windows partition in Ubuntu.

---

### Post by mJayk on 2011-07-06
I think, and its only a "think", if you can locate the .sty package files on you windows system / partition and relocate them to your Ubuntu partition they should work.

I dont think you can tell Tex Live where to look for the package files.

I could be wrong so sorry if I am :)

M

---

### Post by The__Doctor on 2011-07-06
> **mJayk said:**
> I think, and its only a "think", if you can locate the .sty package files on you windows system / partition and relocate them to your Ubuntu partition they should work.
See, I can't really do this because I don't have much space on my Ubuntu partition.

> **mJayk said:**
> I dont think you can tell Tex Live where to look for the package files.
This is what I was hoping I could do. I was hoping I could some way redirect Tex Live to the location of the packages on my Windows partition.

---

### Post by Chronon on 2011-07-07
See if this works:
[http://ubuntuforums.org/showthread.php?t=820426](http://ubuntuforums.org/showthread.php?t=820426)

---

### Post by The__Doctor on 2011-07-08
Hey thanks for the link! It was helpful, though didn't really explain how to make the change. 
```
% The main distribution tree:
TEXMFDIST = /usr/share/texmf-texlive;/media/[Insert Partition Name]/MiKTeX
```Its pretty obvious the change I've made. Basically for anyone who encounters this problem, between each directory add a semicolon, and add it to the TEXFMDIST line. Also, run sudo update-texmf, sudo texhash and sudo mktexlsr.

I also found an alternative solution on this page [https://answers.launchpad.net/ubuntu/+source/revtex/+question/105992](https://answers.launchpad.net/ubuntu/+source/revtex/+question/105992)
pjnoki explains what to do in the second comment. But basically this way uses symbolic links to direct TeX Live to the package on another partition.

---

### Post by Chronon on 2011-07-10
Cool.  I added a section to the wiki.  Please make corrections/clarifications if needed:
[https://help.ubuntu.com/community/LaTeX#Sharing%20packages%20with%20another%20LaTeX%20installation](https://help.ubuntu.com/community/LaTeX#Sharing%20packages%20with%20another%20LaTeX%20installation)

---

### Post by The__Doctor on 2011-07-10
Nice. I didn't edit it cause the instructions are pretty simple. Open the file, add the directory. 

It feels good to have help contribute something to the wiki :D

---

### Post by Chronon on 2011-07-10
Yes it does.  Don't feel shy about making your own edits.  :)

---

