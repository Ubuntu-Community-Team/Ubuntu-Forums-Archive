---
title: "Don't know how to use APT"
date: 2005-08-22
forum: Desktop Environments
---

### Post by MdaG on 2005-08-22
I'm a former Gentoo user. I'm used to Portage. Can anyone point me in the direction of a APT documentation or simply answer how to use it?

I'm trying to install plugins for firefox, java jdk etc. but APT can't find the packages and I don't know how to search among the packages in the repository... any help appreciated.

---

### Post by heimo on 2005-08-22
This is probably handy:
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

---

### Post by MdaG on 2005-08-22
Thanks! Bookmarked that one  :grin:

*edit*
I can't seem to be able to search certain packages that according to this forum should exist.

ex.)

**sudo apt-cache search sun-j2re1.5**

yields nothing...

This is what I've got in my sources.list

[i]deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe[/i]

---

### Post by liquidfire on 2005-08-22
[QUOTE=MdaG]Thanks! Bookmarked that one  :grin:

*edit*
I can't seem to be able to search certain packages that according to this forum should exist.

ex.)

**sudo apt-cache search sun-j2re1.5**

yields nothing...

This is what I've got in my sources.list

[i]deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe[/i][/QUOTE]
 I had the same problem you should compile one from the scratch, be sure too make bin -> deb file. But someone on irc helped me so I don't know if there is an guide.


Step 1 Download the appriopriate file from [www.java.com](www.java.com) for you pc architecture/ubuntu

Step 2 fakeroot make-jpkg j2sdk-something.bin  ## put the name of your java file that you downloaded

Step 3
Install the debial file you created.
Mine would look like this.
sudo dpkg -i sun-j2re1.5_1.5.0+update04_amd64.deb

---

### Post by Lord Illidan on 2005-08-22
Try using the repos in the Ubuntu Guide-- click on the link in my sig..

I think they are in the Restricted Repository...

---

### Post by MdaG on 2005-08-22
Added the repositories you pointed me to, updated apt, but I still don't find any java-jdk...

*edit*
I could download it from sun's website, but then I'd have to set classpath etc. And I don't have a clue how to do that. Is there any official documentation for Ubuntu?

---

### Post by cayamara on 2005-08-22
A great program to apt-get easily is synaptic. Just do a quick```
sudo apt-get install synaptic
```(if not already installed). I love that program.

---

### Post by MdaG on 2005-08-22
I've tried searching for it using synaptic, but I can't find it. I've even followed an online WIKI, but still nothing. How do I install it manually? I've downloaded the binary and extracted it. Now what? I need to put the ~/bin in my local path, but how? Where do I find my local path and what's the syntax?

---

### Post by racecat on 2005-08-22
Hope you don't mind me jumping in here. I'm no expert, but I checked in Synaptic and there is a package called "free-java-sdk". The description (in part) is as follows:

"Complete Java SDK environment consisting of free Java tools
The goal of this package is to be a replacement of commercial Java Source
Development Kits (JDK).  This is accomplished by integrating the best
free java tools into one development environment."

If it is not in your synaptic, you may need to install the expanded repository list. Instructions for this are in the Unofficial Ubuntu Guide.

Hope this helps,
Bill

---

### Post by MdaG on 2005-08-22
I saw that, but I'm not really sure what it is, since I've never heard of it... it's not Blackdown which (as far as I know) is a free java-jdk

*edit*
I used the binary from Sun's webpage and extracted it in a local folder of my user. After that I added the path to my local user's .bashrc. It's ugly, but I don't know how else to do it. I'm not user to running binaries manually. I don't know where all the files end up. It seems like they end up in ONE folder compared to being spread out by software like APT or Portage...

---

### Post by cayamara on 2005-08-28
[QUOTE=MdaG]I saw that, but I'm not really sure what it is, since I've never heard of it... it's not Blackdown which (as far as I know) is a free java-jdk[/QUOTE]
How about
```
$ sudo apt-cache show j2sdk1.4
Package: j2sdk1.4
Priority: optional
Section: multiverse/devel
Installed-Size: 7856
Maintainer: Blackdown Packagers <pkg-j2se-devel@lists.alioth.debian.org>
Architecture: i386
Source: j2se1.4-i586
Version: 1.4.2.02-1
Provides: java-compiler, java2-compiler
Depends: j2re1.4 (= 1.4.2.02-1), libc6 (>= 2.3.4-1)
Pre-Depends: debconf (>= 0.5.0)
Suggests: j2sdk1.4-doc
Filename: pool/multiverse/j/j2se1.4-i586/j2sdk1.4_1.4.2.02-1_i386.deb
Size: 3545144
MD5sum: 0f92ed9f9d089242722931f5c46b54e5
Description: Blackdown Java(TM) 2 SDK, Standard Edition
 The Blackdown Java-Linux Java 2 SDK is a development environment for
 building applications, applets, and components that can be deployed
 on the Java platform.
 .
 The Java 2 SDK software includes tools useful for developing and
 testing programs written in the Java programming language and running
 on the Java platform (this includes the Java 2 Plug-In for Netscape
 and Mozilla browsers).
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```Isn't that exactily what you looked for? I simply searched for "Blackdown" in synaptic. Or, do a quick "apt-cache search blackdown". :razz:

---

