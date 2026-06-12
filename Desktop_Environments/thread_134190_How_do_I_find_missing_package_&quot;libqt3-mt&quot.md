---
title: "How do I find missing package &quot;libqt3-mt&quot;"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Sticky on 2006-02-21
Sorry if this is a really daft question.  I'm a newbie to Ubuntu trying to install Skype following the directions laid out in the [Wiki Howto]("https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29").  I get as far as step 4 where it tells me to install a few dependancies I don't have yet and that's where it all goes wrong.

When I try to install "libqt3-mt" I get a message saying 

"E: Couldn't find package libqt3-mt"

and the process stops.  I've gone on and installed libstdc++5 seperately and tried to insatll Skkype but although the installation seems to work and brings up the Skype icon in the Applications-Internet section it won't actually run.

Can anyone tell me if there is another way I can find and install this missing dependency.

All help gratefully received. :confused:

---

### Post by hajk on 2006-02-21
Are you sure about that? The libqt3-mt package can just be installed with Synaptic, it's in one of the Breezy repositories (main or restricted).

The problem with Skype is that it expects libqt3c192-mt, and that library is not available in Breezy. This is a well-known problem, and it is easily fixed. Install the libqt3-mt package with Synaptic, and (if not already installed) also the packages fakeroot and alien.

The idea is now to let alien first unpack the Skype deb package to a tgz-file, and then to repackage it to a deb file, automatically using the library dependencies in the running system (i.e. Breezy). So, as user:

fakeroot alien --to-tgz skype_1.2.0.18-1_i386.deb
fakeroot alien --to-deb skype-1.2.0.18.tgz

after which the package can be installed with

sudo dpkg -i skype_1.2.0.18-2_all.deb

Note the naming conventions used by alien... Synaptic now lists the package as a "converted Slackware'' package.

Have fun!

---

### Post by aysiu on 2006-02-21
I haven't had any luck with the .deb package for Skype.
Download the Fedora Core 3 .rpm to your desktop and then ```
cd Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i skype*.rpm
```

---

### Post by Sticky on 2006-02-21
Thanks for the replies guys - none of these solutions have worked so far and I've trawled through Synaptic with a fine toothcomb and "libqt3-mt" is definitely not there.  If I require this to make Skype work then I seem to be off to a non-starter.

Any other thoughts.  Surely I should be able to get this package from somewhere (although I wouldn't have the first clue where to put it if I did)?

:confused:

---

### Post by aysiu on 2006-02-21
[QUOTE=Sticky]Thanks for the replies guys - none of these solutions have worked so far[/QUOTE] What error did you get when you tried to install [the Fedora Core 3 RPM](http://www.skype.com/go/getskype-linux-fc2)?

---

### Post by kaamos on 2006-02-21
```
alaisi@ubuntu:~$ apt-cache show libqt3-mt
Package: libqt3-mt
Priority: optional
Section: libs
Installed-Size: 9036
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: qt-x11-free
Version: 3:3.3.4-8ubuntu5
Replaces: qt3-tools (<< 2:3.0.2-20020306-1), libqt3-helper, libqt3, libqt3c102-mt
Depends: libaudio2, libc6 (>= 2.3.4-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libice6, libjpeg62, libmng1 (>= 1.0.3-1), libpng12-0 (>= 1.2.8rel), libsm6, libstdc++6 (>= 4.0.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, zlib1g (>= 1:1.2.1), fontconfig
Suggests: libqt3-mt-psql, libqt3-mt-mysql, libqt3-mt-odbc
Conflicts: libqt3c102-mt, libqui1-emb, libqt3c-mt
Filename: pool/main/q/qt-x11-free/libqt3-mt_3.3.4-8ubuntu5_i386.deb
Size: 3290276
MD5sum: d4e3821610d96c84a9cffaabaa55c730
Description: Qt GUI Library (Threaded runtime version), Version 3
 This is the Trolltech Qt library, version 3. It's necessary for
 applications that link against the libqt-mt.so.3, e.g. all KDE3
 applications.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

alaisi@ubuntu:~$
```

What is your /etc/apt/sources.list ?

---

### Post by Sticky on 2006-02-21
@ aysiu - I didn't get an error on the install.  The application seems fine and the icon appears where it should - when I click on it nothing happens.  I know it says it'll take a minute but I've left it for some time.

@ kaamos - thanks for the code - I presume I can paste that somewhere to use?

I don't really understand the question "What is your /etc/apt/sources.list ?"
I'm a complete newbie when it comes to linux

---

### Post by kaamos on 2006-02-21
Ah, I'm sorry. Neverming that, basicly what I was asking is that have you done this -> [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

And to find out what is wrong with the installed version: Try to open a terminal (Applications->Accessories->Terminal) and type "skype" there. It should show some errors.

Welcome to the forums btw!

---

### Post by Sticky on 2006-02-21
ah - thank you - I will go and read that Howto

For the record, the error message reads

> skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


edit: oh and thanks for the welcome btw :)

---

### Post by Sticky on 2006-02-21
Thank you! Thank you! Thank you!!!!!!!!!!!!!!!!!!!!!

It works - Cheers guys :D :D :D :D

---

