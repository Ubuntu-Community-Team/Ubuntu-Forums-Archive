---
title: "Kubuntu 5.10 Java"
date: 2005-09-19
forum: Desktop Environments
---

### Post by usbsnowcrash on 2005-09-19
First off here is my sources.list
```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```
I am trying to follow the instructions found [here](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)  in order to get java installed but I am running into problems.
I can get fakeroot and java-common installled but no luck on java-package
```

jeff@melchior:~$ sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

``` 
So without this package here is what happens when I try to create the .deb file for java
```

jeff@melchior:~$ fakeroot make-jpkg --full-name "fake" --email "fake@email.com" jdk-1_5_0_05-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found
jeff@melchior:~$

```

So how do I install the java jdk?

---

### Post by aysiu on 2005-09-19
Have you tried following these instructions?

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)
[http://www.frankandjacq.com/ubuntuguide/5.04/#jre](http://www.frankandjacq.com/ubuntuguide/5.04/#jre)

---

### Post by usbsnowcrash on 2005-09-19
[QUOTE=aysiu]Have you tried following these instructions?

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)
[http://www.frankandjacq.com/ubuntuguide/5.04/#jre](http://www.frankandjacq.com/ubuntuguide/5.04/#jre)[/QUOTE]

Well the reason I am trying to do it by hand is because both the jdk and the jre **are missing from the repositories!!!**  
If you don't believe me go look for yourself by browsing the [backports](http://ubuntu-backports.mirrormax.net).  Assuming you can connect to them (I was able to get to it earlier today but now it is gone) you will notice that all kinds of packages are missing like w32codecs and the java packages. 

Anyway I was kinda hesitant to use those repositories anyway since I'm using Breezy and not Horay.  I hope someone resolves this soon!!  I think I may switch to fedora just to get some work done!

---

### Post by aysiu on 2005-09-19
Wow! You're right.

What about [j2rel.4](http://i22.photobucket.com/albums/b337/psychocats/adbe599b.png)?

Would that work for you?

---

### Post by randcoop on 2005-09-19
I've got the win32 codecs and java 1.5 installed on Breezy.  Go to the Sun Java site, download the bin executable file, make it executable (chmod a+x) and run it with sudo ./[name of executable]  

That will install Java.  The word of caution is that it installs to the directory you're in, so if you want it installed to a specific directory, download to that directory.

For the win32 codecs, go the the mplayer site and to the downloads page.  Take the essentials file (it's compressed).  Unzip the files to the /usr/lib/win32 directory (create that directory if you don't already have it).  

That will give you the win32 codecs.

---

### Post by bored2k on 2005-09-19
[http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//java.sun.com/j2se/1.5.0/download.jsp&ei=T4cvQ6jUEqCUsAGH-OCQBw&sig2=tYArH5DRckyNLvyILF_98g](http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//java.sun.com/j2se/1.5.0/download.jsp&ei=T4cvQ6jUEqCUsAGH-OCQBw&sig2=tYArH5DRckyNLvyILF_98g)
Download the .BIN executable
sudo apt-get install fakeroot java-package

Go to the dir where the package is downloaded:
fakeroot make-jpackage FILENAME.bin
sudo dpkg -i *.deb

That will create a debian java package that's easy to manage via Synaptic.

---

### Post by DarkT on 2005-09-20
Ok, first up if you search for it on packages.ubuntu.com (setting breezy as the version) you will get [this](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=java-package&searchon=names&subword=1&version=breezy&release=all) which shows you that java-package is in multiverse so you will have to appened multiverse to  your 
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
```
in the sources.list, or make another new line with just multiverse, depending on what you prefer. Also unless you need them, hash out the deb-src lines as they will only slow down the fetching of package lists when you apt-get update and although it's personal taste I prefer to have multiverse and resticted enabled for all repositories as it can be useful for problems such as this.
 
Now you should be able ot run sudo apt-get update & sudo apt-get install java-package without a problem.
 
I've found there does however seem to be an alternate problem with kubuntu and java. K/Ubuntu seems to install the gij (gnu java interpreter, which is very slow) by default and certain packages are dependent on it being there until sun's java is installed. Now the problem is that gij's  package takes /usr/bin/java as a link to gij so after following the instructions for installing java you will then have to...
 
```

sudo rm /usr/bin/java
sudo ln -s /usr/lib/j2re1.5-sun/bin/java /usr/bin

``` (this may differ depending on which version of java you install.
 
You are now free to remove gij aswell becasue the sun-java fullfills the dependancies of the packages that need gij but you don't have to, they seem to coexist quite happily.

---

