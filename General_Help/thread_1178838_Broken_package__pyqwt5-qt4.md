---
title: "Broken package:  pyqwt5-qt4"
date: 2009-06-04
forum: General Help
---

### Post by bumpkin on 2009-06-04
Tried to install  python-qwt5-qt4 and got the following error. 

python-qwt5-qt4:
  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed

I believe it is looking for python2.5 which I have installed but Jaunty base install uses python 2.6 which is the only thing it can see. 

Anyone know how to fix this?

---

### Post by Megrimn on 2009-06-05
It sounds like you manually downloaded the install file.

did you try looking for a newer version in synaptic?  I found the one you are looking for as I am running Hardy, and I could bet that synaptic would have a version for jaunty.  If not, then I apologize for not being able to help.

---

### Post by bumpkin on 2009-06-05
Yes I installed Synaptic and synaptic will not install it. I'll try the KDE package manager but I think it is the deb package that is the problem it doesn't know to look for Python2.5

---

### Post by SuperSonic4 on 2009-06-05
You might be able to force the installation anyway with the -f flag but that probably isn't wise unless you know what you're doing

---

### Post by mc4man on 2009-06-05
you could go here and try a direct dl and install,  if no, see what error message is presented

[http://packages.ubuntu.com/jaunty/python-qwt5-qt4](http://packages.ubuntu.com/jaunty/python-qwt5-qt4)

are you fully updated and have the 4 ubuntu repos enabled plus jaunty-security and jaunty-updates? (if so run a sudo apt-get update

---

### Post by bumpkin on 2009-06-06
Tried reinstalling python2.5 at the same time installing pyqwt5. No luck. Anyone have a link where I can get the person packaging this to work on a fix?

---

### Post by mc4man on 2009-06-07
You should just ck. that all your jaunty repos are enabled (in System -> Admin. -> Software Sources, on the main page the first 4  and in updates the first 2)
Then do a sudo apt-get update.

I think your confusing python (2.6.2-0ubuntu1) with python2.6, they are 2 different packages

[http://packages.ubuntu.com/jaunty/python](http://packages.ubuntu.com/jaunty/python)

[http://packages.ubuntu.com/jaunty/python2.6](http://packages.ubuntu.com/jaunty/python2.6)

---

### Post by bumpkin on 2009-06-10
Mc4man,

I have enabled all repositories. 
	
>>I think your confusing python (2.6.2-0ubuntu1) with python2.6, they are >>2 different packages

As I read the error message I believe it means that qwt5 depends on python 2.5 and the package is going to install 2.62-0ubuntu1 as a dependency, which according to Synaptic is python 2.6 version 2.62-0ubuntu1. I don't see any other way to read it.

Error message:
python-qwt5-qt4:
Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed

---

### Post by mc4man on 2009-06-10
It does appear to be a currently unresolved issue in jaunty. Python is just a dependency package which in jaunty is 2.6. In the case of  pyqwt5-qt4 having 2.5 installed should of been good enough to install. (except the dep. on python is stopping it.

bug report here
[https://bugs.launchpad.net/ubuntu/+source/pyqwt5/+bug/342782](https://bugs.launchpad.net/ubuntu/+source/pyqwt5/+bug/342782)

I notice for karmic that python2.5 has been added as a dep. 'choice' but for jaunty no fix yet released. ( other than possible workarounds mentioned in link

---

