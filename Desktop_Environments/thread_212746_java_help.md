---
title: "java help"
date: 2006-07-10
forum: Desktop Environments
---

### Post by zapcojake on 2006-07-10
Hello, I am trying to install java on a clean Dapper install and am not having much luck.  I have automatix installed and it keeps giving this error.
SUN JAVA 1.5 JRE
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'.

I have also tried the wiki way without much luck, apt-get tells me java-package is not in the repos.

jake@jake-desktop:~$ uname -r
2.6.15-25-k7
jake@jake-desktop:~$

Is the k7 kernel part of the issue? I downloaded an .386.deb java binary and gdebi won't install, says Error: Dependency is not satisfiable: sun-java-jre
any help is appreciated, thanks

---

### Post by pjbgravely on 2006-07-10
I was getting crazy dependancy errors too. The fix for me was to remove the .us in the front of the repository URL's in /etc/apt/sources.list


Paul

---

### Post by codypumper on 2006-07-10
Instead of installing with Automatix do the following:
-Download [http://jdl.sun.com/webapps/download/AutoDL?BundleId=10541](http://jdl.sun.com/webapps/download/AutoDL?BundleId=10541) to your desktop.
-Open a terminal
-type the following in terminal:
   cd Desktop
   sh jre-1_5_0_07-linux-i586-rpm.bin
   sudo alien jre-1_5_0_07-linux-i586.rpm
-then double click on the .deb file on your desktop

If that doesn't work, tell me. After installation you can delete all the files off of your desktop.

---

### Post by ElijahLofgren on 2006-07-10
> **zapcojake said:**
> Hello, I am trying to install java on a clean Dapper install and am not having much luck
....
any help is appreciated, thanks
Java made it into the Ubuntu universe repository a while back and that has made it *much* easier to install.

Following this works for me on a fresh Dapper install: [http://www.elijahlofgren.com/linux/ubuntu/multimedia/#java-plugin](http://www.elijahlofgren.com/linux/ubuntu/multimedia/#java-plugin)

Basically the instructions say to enable the Ubuntu universe repository and then run:

```
sudo apt-get install sun-java5-plugin
```

Then restart Firefox.

Hope this helps. ;)

---

### Post by zapcojake on 2006-07-11
I got the rpm converted to  .deb and installed but now this happens
jake@jake-desktop:~/Desktop$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.5.0_07/bin/
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)  [/usr/java/jre1.5.0_07/bin/java = Error]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by ElijahLofgren on 2006-07-11
> **zapcojake said:**
> I got the rpm converted to  .deb and installed but now this happens
jake@jake-desktop:~/Desktop$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)


I'd try installing  sun-java5-jre from the Ubuntu multiverse repository:
```

sudo apt-get install sun-java5-jre

```

Info about it:
> 
$ apt-cache show sun-java5-jre
Package: sun-java5-jre
Priority: optional
Section: multiverse/libs
Installed-Size: 15768
Maintainer: Matthias Klose <doko@ubuntu.com>
Architecture: all
Source: sun-java5
Version: 1.5.0-06-1
Replaces: sun-java5-bin, ia32-sun-java5-bin
Provides: java-virtual-machine, java2-runtime
Depends: java-common, locales, sun-java5-bin (= 1.5.0-06-1) | ia32-sun-java5-bin (= 1.5.0-06-1), debconf (>= 0.5) | debconf-2.0
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Recommends: java-common (>= 0.24), gsfonts-x11
Suggests: sun-java5-plugin | ia32-sun-java5-plugin, sun-java5-fonts, ttf-baekmuk, ttf-kochi-gothic | ttf-kochi-gothic-naga10, ttf-kochi-mincho | ttf-kochi-mincho-naga10, ttf-arphic-bsmi00lp
Conflicts: j2se-common
Filename: pool/multiverse/s/sun-java5/sun-java5-jre_1.5.0-06-1_all.deb
Size: 7341172
MD5sum: 321431e1e47c0a51902fe598773af1f7
Description: Sun Java(TM) Runtime Environment (JRE) 5.0
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 5.0
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 5.0
 (package sun-java5-jdk).
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package
 .
 This package contains architecture independent files.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu



---

### Post by acorn22 on 2006-07-11
<ignore>

---

### Post by zapcojake on 2006-07-12
Here's what happens 
jake@jake-desktop:~$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
jake@jake-desktop:~$
 Heres my sources.list



## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports multiverse universe main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

##############################
### Automatix Repositories ###
##############################

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
## created by automatixrepo2

---

### Post by ElijahLofgren on 2006-07-13
> **zapcojake said:**
> Here's what happens 
jake@jake-desktop:~$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
jake@jake-desktop:~$
 Heres my sources.list



## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


Hmm.. That's odd. Because it looks like you have the "multiverse" 
repository enabled. And sun-java5-jre is in that repository: [http://packages.ubuntu.com/dapper/libs/sun-java5-jre](http://packages.ubuntu.com/dapper/libs/sun-java5-jre)

I would make sure your package list is up to date by running:
```
sudo apt-get update
```

If it doesn't work after that then you could manaully download and install the deb:
[http://ftp.cs.umn.edu/pub/ubuntu/pool/multiverse/s/sun-java5/sun-java5-jre_1.5.0-06-1_all.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/multiverse/s/sun-java5/sun-java5-jre_1.5.0-06-1_all.deb)

But if you do it that way you'll likely have to track down a bunch of other dependency packages to download from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by zapcojake on 2006-07-13
this is the results of apt-get update
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ElijahLofgren on 2006-07-13
> **zapcojake said:**
> this is the results of apt-get update
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Hmm.. This is an odd problem. I am able to apt-get update just fine.

I found some threads where other people mention having this type of problem:

Is multiverse down?: [http://www.ubuntuforums.org/showthread.php?t=193638](http://www.ubuntuforums.org/showthread.php?t=193638)

In the above thread it sounds like trying a different mirror worked.

Re: gzip trouble with apt-get update
[http://www.ubuntuforums.org/showthread.php?t=9944#10](http://www.ubuntuforums.org/showthread.php?t=9944#10)

In the above post sounds like this person was having a problem with their "proxy content filter" blocking .bz2 files.

The solution was to change http:// URLs to ftp:// URLs in /etc/apt/sources.list.

So I would try changing the following:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


to this:
> 
deb [ftp://archive.ubuntu.com/ubuntu](ftp://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu](ftp://archive.ubuntu.com/ubuntu) dapper multiverse


**Edit: Update: **I just tried using the sources.list that you pasted and I was able to reproduce a problem very similar to yours. It seems that you have some repositories listed twice. I'll figure out the correct sources.list for you to use and paste it in a new post. **Stay tuned...**

**Update 2:** Weird, without changing the sources.list file I ran "sudo apt-get update" again and didn't get those errors. :???:  Do you mind trying running "sudo apt-get update" yet again?

I guess it could be a flakey Internet connection.

**Update 3:** I ran sudo apt-get update yet again and this time I got those error again. I guess the duplicate repository entries could be causing this somewhat "random" problem. I'll try finding and removing the duplicate ones. ;)

---

### Post by ElijahLofgren on 2006-07-13
It seems as though my advice has caused you problems. :(  Sorry about that.

Automatix had already enabled the universe and multiverse repositories for you, so when you added them in again I think it caused your problem.

In my advice on my website about adding more repositories I forgot to add a warning to only add them if they are not already enabled. I have corrected that: [http://www.elijahlofgren.com/linux/ubuntu/#more-software](http://www.elijahlofgren.com/linux/ubuntu/#more-software)

Try **removing** the following lines from your sources.list and then running sudo apt-get update again:

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


---

### Post by zapcojake on 2006-07-14
> It seems as though my advice has caused you problems.  Sorry about that.


no sweat, I guess we both learned a little which is how its done.  Thanks

---

