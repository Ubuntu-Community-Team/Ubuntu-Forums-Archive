---
title: "Skype - did installation fail?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by atheist on 2006-04-03
Hello everyone,

I tried to install Skype as it was discribed in the link: [https://wiki.ubuntu.com/SkypeHowto?](https://wiki.ubuntu.com/SkypeHowto?) 


It seems ddid not work, - I got the message:

ubuntu@ubuntu:~$  sudo dpkg --install skype_1.2.0.18-2_i386.deb
Password:
Selecting previously deselected package skype.
(Reading database ... 71426 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-2_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
ubuntu@ubuntu:~$


What I do next?
Thank you in advance

---

### Post by Princey on 2006-04-03
> **atheist]Hello everyone,

I tried to install Skype as it was discribed in the link: [https://wiki.ubuntu.com/SkypeHowto?](https://wiki.ubuntu.com/SkypeHowto?) 


It seems ddid not work, - I got the message:

ubuntu@ubuntu:~$  sudo dpkg --install skype_1.2.0.18-2_i386.deb
Password:
Selecting previously deselected package skype.
(Reading database ... 71426 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-2_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1) said:**
> 

You can either try this [QUOTE]sudo apt-get install -f and it will fix the broken dependencies for you or you can use Automatix [http://www.ubuntuforums.org/showthread.php?t=138405]("http://www.ubuntuforums.org/showthread.php?t=138405") to do the job for you. Automatix should help you install most of the stuff you might struggle early on with like flash and plugins.

---

### Post by ronmarley1 on 2006-04-03
Skype needs the libstdc++5 package.  You can install it using the Synaptic Package Manager (which is under System -->Administration).  Or, you can type ```
sudo apt-get install libstdc++5

``` in a terminal window.  After doing either of these, run the Skype install as you did.  However, if there are other dependencies, you will need to install those also.  Lastly, you may want to look at Automatix.  It's an installation script that will install Skype and a bunch of other "essential" items.  Please read the thread befor installing Automatix.  Some folks don't like it (I do).  Here's the link to Automatix -->[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

