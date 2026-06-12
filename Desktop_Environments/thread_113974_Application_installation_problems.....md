---
title: "Application installation problems...."
date: 2006-01-07
forum: Desktop Environments
---

### Post by Razorback on 2006-01-07
I am having problems installing a few applications and am stuck as to what I am doing wrong.  I want to install Thunderbird, Firestarter, clamAV, etc.  I am following the installation instructions but am getting errors.

Thunderbird:
pcuser@ubuntu:~/Apps$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate

firestarter:
pcuser@ubuntu:~/Apps/firestarter-1.0.3$ ./configure
checking for intltool >= 0.30... 0.31.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool

I found the perl folder so it does exist.  Thunderbird - I have no idea.
Do you have to unzip apps in a specific directory or can they go in any directory?
I tried synaptic but had no luck.  I am new to linux so I apologize if I have missed something really obvious.  Any help would be appreciated.  On another note, I saw  where someone mentioned getting all the repositories available for access to lots of apps.  How can I get these?  TIA for any help.

---

### Post by zappa86 on 2006-01-07
Did you make sure to add the extra repositories?
[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")
[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

You can also add them by doing a:
```
sudo gedit /etc/apt/sources.list
```
and uncommenting them (they will be the lines that start with deb)

As soon as you add them you should make sure to update the list by doing a:
```
sudo apt-get update
```

also you can get firestarter for the repositories so you dont have to make it yourself.

---

### Post by Razorback on 2006-01-07
Thank you.  I just updated and going to check it out. :)

---

