---
title: "dpkg apt errors! please help!"
date: 2005-05-01
forum: Desktop Environments
---

### Post by stepper on 2005-05-01
Hi, I have this serious problem with apt-get & dpkg:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gstreamer0.8-lame libxvidcore4 mozilla-acroread mplayer-386
The following packages will be upgraded:
  acroread acroread-plugins kdelibs-bin kdelibs-data kdelibs4 openoffice.org
  openoffice.org-bin openoffice.org-gtk-gnome openoffice.org-l10n-en
  openoffice.org-thesaurus-en-us ttf-opensymbol w32codecs
12 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/125MB of archives.
After unpacking 184kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/acroread-plugins_7.0-0sarge0.9_i386.deb (--unpack):
 **files list file for package `gdm' is missing final newline**
Errors were encountered while processing:
 /var/cache/apt/archives/acroread-plugins_7.0-0sarge0.9_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Yes I did search the forums and google and all I could find was this threads and I got no help:

[http://ubuntuforums.org/showthread.php?t=30929&highlight=dpkg+apt+error](http://ubuntuforums.org/showthread.php?t=30929&highlight=dpkg+apt+error)

[http://ubuntuforums.org/showthread.php?t=21981&highlight=dpkg+apt+error](http://ubuntuforums.org/showthread.php?t=21981&highlight=dpkg+apt+error)

[http://ubuntuforums.org/showthread.php?t=21106&highlight=dpkg+apt+error](http://ubuntuforums.org/showthread.php?t=21106&highlight=dpkg+apt+error)

---

### Post by Professor X on 2005-05-01
See if this fixes it:

```
cd /var/cache/apt/archives
dpkg -i --force-overwrite acroread-plugins_7.0-0sarge0.9_i386.deb
dpkg --configure -a
```

---

### Post by stepper on 2005-05-01
No, I still get the same error about 'gdm' missing final newline!

---

### Post by Professor X on 2005-05-01
Try deleting /var/lib/dpkg/info/gdm.list.

---

### Post by stepper on 2005-05-01
[QUOTE=Professor X]Try deleting /var/lib/dpkg/info/gdm.list.[/QUOTE]
NO go! New error about 'gettext-base' is missing final newline.

---

### Post by Professor X on 2005-05-01
Well for some reason your package database is corrupted.  You could try moving the whole directory /var/lib/dpkg/info and then doing an apt-get update.  Can't promise anythign though.

---

### Post by az on 2005-05-01
No.  No!

sudo dpkg --clear-avail

Do you have any funny repos in your sources.list?  (acroread?)

---

### Post by stepper on 2005-05-02
[QUOTE=azz]No.  No!

sudo dpkg --clear-avail

Do you have any funny repos in your sources.list?  (acroread?)[/QUOTE]
I'm still getting the same 'gdm' is missing final newline.
I didn't understand your question about funny repos so anyway here's my sources.list:
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

```

---

### Post by stepper on 2005-05-08
*bump*

Sorry to bump this thread but I'm still struggling and I can't install anything.
Also there is this error about Eterm.png missing when gdm starts! Is this somehow related to my problem?

---

### Post by bigbangbigbigbang on 2005-05-08
[QUOTE=stepper]I'm still getting the same 'gdm' is missing final newline.
I didn't understand your question about funny repos so anyway here's my sources.list:
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

```[/QUOTE]

Hey, Ubuntu IS based on debian unstable, you MUST NOT have stable and testing in your sources.list! If you need Marillat's sources (which are great in general) you have to use ONLY the unstable branch.

---

