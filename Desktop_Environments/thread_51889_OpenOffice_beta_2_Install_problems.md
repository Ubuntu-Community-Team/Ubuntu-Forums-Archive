---
title: "OpenOffice beta 2 Install problems"
date: 2005-07-25
forum: Desktop Environments
---

### Post by alquimista on 2005-07-25
Hi,
I'm new to Linux and I'm playing with Kubuntu installed in a Toshiba Satellite notebook; I'm ntrying to access all my OOffice 2 documents, yet I have had problems installing OO 2 under Kubuntu:
I  followed the documented steps to install it, yet executing 
 alien -k *.i586.rpm" 

I got the following log:

-----------------
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/openofficeorg-base
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: failure: chown new files list file: Operación no permitida
dh_gencontrol: command returned error code 256
make: *** [binary-arch] Error 1
find: openofficeorg-base-1.9.118: No existe el fichero o el directorio
----------------- 

Any help will be appreciated,
Thank you,
Guillermo

---

### Post by GTvulse on 2005-07-25
You need to run alien under fakeroot. Like this:
```
-$ fakeroot alien -d --fixperms *.rpm
-$ sudo alien -i *.deb desktop-integration/*.deb
-$ sudo chmod 755 /opt/openoffice*/program/soffice

```

---

### Post by alquimista on 2005-07-26
Hola Alejo,

Thanx for the answer; it worked for me  O:) . Yet when I start any OO 2 aplication, I get the initial OO Office window with a wired font like Windings, and nothing can be understood  :neutral: . Maybe a font file is missing? I'm using Kubuntu.


Guillermo

---

### Post by GTvulse on 2005-07-26
Hola Guillermo,

You may need to install some basic Gnome libraries for OOo2 to work. I'm guessing (as I'm at the windows partition at the moment :-)), but I'd think that at least you need to install the pango runtime and dependencies.

BTW, build118 has some missing macro libraries related to the Form Wizrd so you'll get some eror messages during operation. Till now they have not been anything but annoying messages for me either in Ubuntu or WinXP. A packaging bug that will be fixed in the next build (next week I think). When you come to that update time, remove first the previous version of OOo2, it is very easy if using Synaptic as all appear grouped under "rpms converted with alien" or something like that. Kynaptic is quite lacking, so you may want to install Syanptic anyway (and that would pull in the needed gtk/gnome libraries for proper OOo operation).

---

### Post by alquimista on 2005-07-26
Thank you Alejo,

I changed Kubuntu-KDE-desktop fonts and I got OO2 readable; yet when installing the spanish languaje package, I got:

Unpacking and installing...
openofficeorg-es-res-1.9.118-1.i586.rpm
openofficeorg-es-1.9.118-1.i586.rpm
openofficeorg-es-help-1.9.118-1.i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No existe el fichero o el directorio (2)
error: cannot open Packages database in /var/lib/rpm
Done... 

Should I adjust the ".sh" file to have it working? what sort of changes would they be?

Thank you,
Guillermo

---

### Post by GTvulse on 2005-07-27
Good question! That's the one thing I haven't figured out yet. Doesn't affect me that much though, I use the English interface and only have immediate need for the dictionaries... But that's no excuse. Hmmm.. I guess we both should file a bug report at OpenOffice (dos golondrinas si hacen más verano :-).

---

### Post by GTvulse on 2005-07-27
Found a way! The original posting is at [http://br-linux.org/linux/?q=node/672](http://br-linux.org/linux/?q=node/672):

```

jauja:~$ grep -ina linenum OOo_1.9.118_LinuxIntel_langpack_es.sh
11:linenum=155
135:  $tail_prog +$linenum $0 | gunzip | (cd $outdir; tar xvf -)
141:  $tail_prog +$linenum $0 | gunzip | (cd $outdir; tar xvf -)

```

```
jauja:~$ tail -n +155 OOo_1.9.118_LinuxIntel_langpack_es.sh | gunzip | (tar xvf -)
openofficeorg-es-res-1.9.118-1.i586.rpm
openofficeorg-es-1.9.118-1.i586.rpm
openofficeorg-es-help-1.9.118-1.i586.rpm

```

```
jauja:~$ fakeroot alien -d --fixperms *.rpm
openofficeorg-es_1.9.118-2_i386.deb generated
openofficeorg-es-help_1.9.118-2_i386.deb generated
openofficeorg-es-res_1.9.118-2_i386.deb generated

```

```
jauja:~$ sudo dpkg -i *.deb
Selecting previously deselected package openofficeorg-es.
(Reading database ... 72752 files and directories currently installed.)
Unpacking openofficeorg-es (from openofficeorg-es_1.9.118-2_i386.deb) ...
Selecting previously deselected package openofficeorg-es-help.
Unpacking openofficeorg-es-help (from openofficeorg-es-help_1.9.118-2_i386.deb) ...
Selecting previously deselected package openofficeorg-es-res.
Unpacking openofficeorg-es-res (from openofficeorg-es-res_1.9.118-2_i386.deb) ...
Setting up openofficeorg-es (1.9.118-2) ...
Setting up openofficeorg-es-help (1.9.118-2) ...
Setting up openofficeorg-es-res (1.9.118-2) ...

```

And bingo!

---------
**NOTE**: Since build 1.9.122 this method  to install a language pack isn't needed anymore. Now language packs are rpms bundled in a tar and gziped file, therefore one only needs to unpack and convert them with alien to later install with dpkg, as described above for the main installer rpms.

---

### Post by alquimista on 2005-07-27
Alejo !!!
Thank you very much indeed !! worked just fine !

Abrazo !
Guillermo

---

### Post by alquimista on 2005-07-27
Alejo,

Sorry ot bother you; you have helped me a lot, so I'm gratefull to you. I'll bother you  again with something that anoys me and that's theOO font. It apperas with big letters and some of them are not well displayed like letter "r". When I open a document at 75% I just can read it. 
You recomended me to unload basic GNome libraries using Synaptic; then I'll search for "pango runtime and dependencies". Sorry for the naive questions since I'm new in Linux, but how can I make synaptic work? Once I donlowaded it using Kynaptics I looked for it in the system menu and was not there. Is it a command line operation? if so, what parameter should I write to download pango?

Thank you,
Guillermo

---

### Post by GTvulse on 2005-07-27
Guillermo,

you'll need to add it to your K Menu (I'm not very handy with KDE, rather Gnome so you'll forgive my naiveté on this issue :-)).  On the font matter, there is a way to integrate gnome applications to KDE by installing "gtk2-engines-gtk-qt". After your do, you'll notice a new panel in KDE's control center, you'll be able to tweak the appearance of Gnome aplications there (and that will pull in other Gnome libraries you may be needing as well).

---

