---
title: "How to install jdk1.5.0_05 please??"
date: 2006-01-04
forum: General Help
---

### Post by jrios_03 on 2006-01-04
Hi everyone...

I'm new in UBUNTU and Linux, I'm a java programer and I want to know how to install the jdk1.5.0_05 and run it...

I try to install the .bin file, but when I try to compile or run a file the terminal give me an error, and I don't understand the error...

Please help me... it's very important to me...

Sorry for my english, I'm Chilean...

Grettings...

---

### Post by gingermark on 2006-01-04
Hi there!

There was a request for version 1.5.0_04 to be added to the backport repository (see [this thread](http://ubuntuforums.org/showthread.php?t=44182)). Unfortunately it doesn't seem to be there yet.

It's always easier to install packages from the repositories, so if 1.5.0_04 is ok then I think the best course of action is to post in that thread asking for an update.

Otherwise, try posting the error message here and I'm sure someone will help you compile it yourself.

---

### Post by Pawel Stolowski on 2006-01-05
Use Penguin Liberation Front repository - this is a nice repo with some non-free stuff for ubuntu, like sun java (jre and sdk), libdvdcss2, w32codecs etc. It is by the way now the preferred repo for this kind of stuff instead of debian-marillat repository (which may cause problems in ubuntu).

Add one of them:

## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

Then
sudo apt-get install sun-j2sdk1.5

For more information see: [http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by Luke on 2006-01-05
check this wiki entry
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by noigeaR on 2006-01-05
[QUOTE=jrios_03]I try to install the .bin file, but when I try to compile or run a file the terminal give me an error, and I don't understand the error...
[/QUOTE]
Follow the instructions from this **[How-To]("http://www.ubuntuforums.org/showthread.php?t=76735")**, then it should work. You probably forgot to use fakeroot or update your alternatives or something.
The How-To is for the JRE, but installing the SDK works the same way, just replace all the JRE filenames by the SDK filenames and you maybe have to run an additional command if more than one java compiler is installed on your system and that's ```
sudo update-alternatives --config javac
```
Notice the c in javac (in the How-To they only update-alternatives for java).

Building your own packages from the .bin is currently the only way to get the 1.5.0_06 version of the Sun Java SDK. Ubuntu PLF is still at 1.5.0_05 at the moment.

---

