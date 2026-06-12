---
title: "Please help me install Matplotlib 0.98 on Hardy Heron"
date: 2009-04-12
forum: General Help
---

### Post by fluoborate on 2009-04-12
Hello Everyone,

I have wasted several days trying to get Matplotlib 0.98.5.2 installed on Ubuntu Server 8.04 Hardy Heron. I really, really want Matplotlib 0.98. Here is what I have tried:

sudo apt-get install python-matplotlib
#Gets and properly installs Matplotlib 0.91, which is
#not good enough for my purposes because it handles
#dates poorly

wget [http://.....matplotlib-0.98.5.2.tar.gz](http://.....matplotlib-0.98.5.2.tar.gz)
tar xvzf matplotlib-0.98.5.2.tar.gz
cd matplotlib-0.98.5.2
python setup.py build
#It wants Numpy 1.1, this machine only has Numpy 1.0.4 because
#that is all I can get with apt-get. I wish I could apt-get
#a later version of Numpy.

#Okay, I download and unzip Numpy as above, and then
python setup.py build
#Numpy can't find Python.h, "build" fails
#"find" has no trouble finding Python.h, in the
#"includes" directory, where it should be.
#After a long time, I read on the internet that I 
#need to install gcc, I do, and the error changes:
#Numpy "can't check configuration"
#What the hell? How do I fix this?

Even if I can fix this one Numpy problem, I bet I will find another problem in another prerequisite that Matplotlib needs. This is so hard, and so annoying, I have encountered and tackled a half dozen bugs in the past few days, but I really haven't made any progress because I still don't have Matplotlib 0.98 installed.

Please, please help.

There is a Jaunty package that installs Matplotlib 0.98, how can I install that Jaunty package on a Heron machine? I tried modifying /etc/apt/preferences, but I couldn't make it work right. I couldn't find a .deb file of the Jaunty package.

Should I just upgrade to Jaunty? I chose Heron because this is a server, and Heron is a Long-term support version. Can I upgrade the Jaunty without breaking anything, and how? All I have on this server is Django 1.0.2, Apache 2, MySQL, and all the stuff they need to talk (mod_python, python-sqldb).

Again, please help. I am almost ready to smash this server with a crowbar, all because of dates in Matplotlib.

---

### Post by mc4man on 2009-04-12
because my hardy is my main use and setup very well i don't want to fool around to much.
As far as your numpy 1.1 you can install the intrepid version on hardy if you install the intrepid libgfortran3_4.3.2

whether or not you 'dead end' after that I can't say (i did install the 2 linked below

[http://packages.ubuntu.com/intrepid/libgfortran3](http://packages.ubuntu.com/intrepid/libgfortran3)

[http://packages.ubuntu.com/intrepid/python-numpy](http://packages.ubuntu.com/intrepid/python-numpy)

Good luck

---

### Post by maheshasolkar on 2009-04-12
A .deb for i386 binary package for Jaunty is available at:

  [https://launchpad.net/ubuntu/jaunty/i386/python-matplotlib/0.98.5.2-1ubuntu3](https://launchpad.net/ubuntu/jaunty/i386/python-matplotlib/0.98.5.2-1ubuntu3)

However, I am not sure of the consequences of intalling Jaunty package on Hardy. I think you should make sure that is won't cause any problems, before installing it.

I hope someone more knowledgeable will respond soon.

---

### Post by fluoborate on 2009-04-12
I tried to install the .deb of Matplotlib 0.98 for Jaunty, but it failed because it didn't have Numpy >= 1.1 (it has 1.0.4). Where can I find a .deb of Numpy 1.1?

In general, where can I find .deb files of things? The .orig, .diff, and .dsc will not allow me to do a dpkg install, right? So, we are still left with me needing to install Numpy...

Thanks, I wouldn't have found the Matplotlib .deb otherwise.

---

### Post by fluoborate on 2009-04-12
Oh, the .deb files are all here:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

There may be other repositories, so please do share.

I got a .deb file of Numpy, it installed fine, and then:
fluoborate$ python
>>>import numpy
>>>numpy.__version__
'1.1.0'

#Eureka!

Matplotlib 0.98 still isn't working, but I have made what is hopefully a big step. I found a .deb of it, but it says it needs more packages.

Should Aptitude fix this somehow? I am just using dpkg from the command line at the moment.

---

### Post by fluoborate on 2009-04-12
More progress!

I have successfully installed matplotlib 0.98, but when I tried to start up Apache and serve a Django site that uses it... Apache wouldn't reload.

Here is how I installed Matplotlib. I recursively did the following:

```
function install(package(n)):
   wget http://http.us.debian.org/package(n)_i386.deb
   function attempt(package(n)):
      sudo dpkg --install package(n)_i386.deb
      if: "Error, package(n) requires package(n+1)"
      then:
         install(package(n+1))
         attempt(package(n))
      else:
         #package(n) has been successfully installed, continue to
         #the next iteration of the parent loop.
```

That's two recursive loops:

1. The install() loop iterates multiple times when there is a package (that depends on a package){n}. #This is regex syntax.

2. The attempt() loop iterates multiple times when a package depends on another package (, and also this other package){n}.

I got several iterations deep in both loops. I felt like a Turing machine. I have more sympathy for computers now.

---

### Post by fluoborate on 2009-04-12
How many hours has this been? I have been working at this CONTINUOUSLY since my first posting.

I had it up to Matplotlib 0.98.1 and working perfectly. But 0.98.1 had one bug with axvline(), and I knew that 0.9.5.2 fixed this bug because I originally wrote the code for that version. So I had to upgrade.

While trying to upgrade from 0.98.1 to 0.98.5.2, I finally got fed up, added a new source to sources.list, and did aptitude install python-matplotlib. It tried, but the install of Matplotlib was broken. While fixing it, I somehow downgraded all the way to 0.91.

CRAP!

This is really annoying. How do I FORCE Aptitude to download the newer python-matplotlib, when it sees two options?

---

### Post by fluoborate on 2009-04-14
All fixed, all working fine now. It was just a massive pain, there is no good advice that I can give to the next person who encounters a similar problem.

---

