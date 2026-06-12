---
title: "Klibido"
date: 2005-04-10
forum: Desktop Environments
---

### Post by rigga on 2005-04-10
Has anyone managed to get klibido to work? when I go to install it states:

klibido: Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed

I have manually installed the latest version of that library (0.5.14) and manually installed klibido however just after going through the initial preference screen the app crashes, any one managed to get it to work?

Cheers

Edit: Resolved by removing libidn11-dev and reinstalling - works fine now

---

### Post by QCompson on 2005-04-15
I had the exact same experience... it's unfortunate because I find pan (aside from being gtk in kde environment) to be a resource-hog, and I'd like to try a different newsreader.

---

### Post by NTolerance on 2005-04-26
I'm still getting the crashing even after removing the package you mentioned and reinstalling both it and/or klibido.  Any ideas?  

I'm using the Debian klibido package.

---

### Post by rigga on 2005-04-26
Have you now tried installing the version shown in kpackage ?

---

### Post by djpate on 2005-04-26
[QUOTE=NTolerance]I'm still getting the crashing even after removing the package you mentioned and reinstalling both it and/or klibido.  Any ideas?  

I'm using the Debian klibido package.[/QUOTE]
 same here , tried from source but no luck either !
anyone has a solution?

---

### Post by simba on 2005-05-03
I have also noticed this problem.

I've tested the package klibido_0.2.2.2-0ubuntu1_i386.deb from StephanHermann ([https://www.ubuntulinux.org/wiki/MOTUNewPackages)](https://www.ubuntulinux.org/wiki/MOTUNewPackages)), but I have the following errors :

dpkg - warning: ignoring request to remove klibido which isn't installed.
root@ubuntu:/home/simba # dpkg -i klibido_0.2.2.2-0ubuntu1_i386.deb
Selecting previously deselected package klibido.
(Reading database ... 66217 files and directories currently installed.)
Unpacking klibido (from klibido_0.2.2.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of klibido:
 klibido depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 klibido depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 klibido depends on libidn11 (>= 0.5.13); however:
  Version of libidn11 on system is 0.5.2-3.
dpkg: error processing klibido (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 klibido

I don't understand, because I should have the last versions of the ubuntu libraries.
My source.list is like this one : [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

How can I optain newer unbuntu libs ?
I don't understand why does the packager package programs for ubuntu with dependencies to packages not yet available in the distribution...

---

### Post by rigga on 2005-05-04
After you updated the libidn11 and installed the klibido that is in the package manager did you delete your exisiting .klibido folder from your home directory before running the klibido again?

---

### Post by oldblue on 2005-05-10
Simba, install the necessary packages from Ubuntu.  Klibido will then complain about wrong version numbers, etc.  if you use the command "dpkg -i --force-depends [Klibido filename]", all those errors will turn into warnings and it should install.  I don't recommend ever using that command, but this is an end user application that just  downloads stuff, so if it messes up it shouldn't screw with your system.  I'm running it like this right now and it seems to be working.

Good Luck

---

### Post by oldblue on 2005-05-10
Hmmm....actually this seems to break apt-get.  If you use my method Synaptic will uninstall Klibido before installing/uninstalling any other application.  Anyone know how to make apt-get ignore it as a broken package?

---

### Post by oldblue on 2005-05-10
Well, if anyone is still interested in this program, go to klibido.sf.net.  In the download section they explain that the Debian package will not work on Ubuntu and they give instructions on how to compile it for Ubuntu using apt-build from a third party Debian repository.

All this trouble for one little program   ](*,)

---

### Post by babwe on 2006-03-18
I had this problem just do this from terminal
sudo apt-get build-deb klibido
and wolla it installs

---

