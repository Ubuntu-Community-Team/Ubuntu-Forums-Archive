---
title: "I am stuck deep in mud (or how do you use a new package)"
date: 2005-09-15
forum: Desktop Environments
---

### Post by svetlo56 on 2005-09-15
I downloaded the CTN package from the Debian repository and installed without problems. Synaptic package manager duly shows it as installed properly.

Now I have no idea how to start the program and change the parameters. I am new to Linux and guess this is more a general question: once you install a new application, how do you start (use) it? My package does not show in the menus and I do not know how to get it to the menus, or to the desktop, which would be the preferred place on my system.

---

### Post by bionnaki on 2005-09-15
check /usr/bin 
that's where the "executables" often end up
then just link your icons to that.

---

### Post by er4z0r on 2005-09-15
In general you have the following possibilties to get this kind of info (how to launch program XY)

[list]
[*]apt-cache show <package-name> provides you with info about the **package** 
[*]look in /usr/share/doc/<packagename>. Here you should find documentation (read with less or zless)
[*]if its an application look in the bin and sbin directories for the executable
[/list] 

And of course there is man and info ;)

---

### Post by svetlo56 on 2005-09-15
[QUOTE=er4z0r]In general you have the following possibilties to get this kind of info (how to launch program XY)

[list]
[*]apt-cache show <package-name> provides you with info about the **package** 
[*]look in /usr/share/doc/<packagename>. Here you should find documentation (read with less or zless)
[*]if its an application look in the bin and sbin directories for the executable
[/list] 

And of course there is man and info ;)[/QUOTE]

I can't find the thing in either of these directories. And I get

root@ubuntu1:/home/djordje# apt-cache show ctn
Package: ctn
Priority: extra
Section: universe/graphics
Installed-Size: 17156
Maintainer: Thijs Kinkhorst <kink@squirrelmail.org>
Architecture: i386
Version: 3.0.6-3
Depends: libmysqlclient14, lesstif1, libxaw7, xlibs
Suggests: ctn-doc
Filename: pool/universe/c/ctn/ctn_3.0.6-3_i386.deb
Size: 4398868
MD5sum: 30c250913d8f3bff80e8e9502a99e973
Description: Runtime files for Central Test Node, a DICOM implementation
 DICOM is the standard for image storage, annotation, and networking.
 It is used widely for medical imaging.
 .
 This package includes the binary and run-time configuration files for CTN.
 .
 The home page for CTN is [http://www.erl.wustl.edu/DICOM/ctn.html](http://www.erl.wustl.edu/DICOM/ctn.html).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

root@ubuntu1:/home/djordje#

So this is not helpful. 

 ](*,)

---

### Post by az on 2005-09-15
[QUOTE=svetlo56]I downloaded the CTN package from the Debian repository and installed without problems. Synaptic package manager duly shows it as installed properly.

Now I have no idea how to start the program and change the parameters. I am new to Linux and guess this is more a general question: once you install a new application, how do you start (use) it? My package does not show in the menus and I do not know how to get it to the menus, or to the desktop, which would be the preferred place on my system.[/QUOTE]

Is it not in the Ubuntu universe repositories?  That may be your problem.

dpkg -L (package) shows a list of files in a package.  Find the executable in that list.

(Note that it is a capital "L")

---

