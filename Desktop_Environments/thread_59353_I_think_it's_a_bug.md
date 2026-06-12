---
title: "I think it's a bug"
date: 2005-08-23
forum: Desktop Environments
---

### Post by Luzbel on 2005-08-23
First, my repositories:

cat /etc/apt/sources.list
____________________________________________________________________________________

#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# NORMALES

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

# ARREGLO DE ERRORES

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse

# SEGURIDAD

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

# BACKPORTS

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

# RAMA INESTABLE

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

# KDE 3.4.2 KUBUNTU

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

# MARILLAT

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

# XDTV

deb [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) binary/
deb-src [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) source/
deb [ftp://ftp.las.ic.unicamp.br/pub/debian.d/debian-marillat](ftp://ftp.las.ic.unicamp.br/pub/debian.d/debian-marillat) unstable main
deb-src [http://perso.wanadoo.fr/debian/](http://perso.wanadoo.fr/debian/) unstable main

# RAREWARES

#deb [http://rarewares.org/debian/packages/stable/](http://rarewares.org/debian/packages/stable/) ./
#deb [http://rarewares.org/debian/packages/unstable/](http://rarewares.org/debian/packages/unstable/) ./

# WINEHQ

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
_________________________________________________________________

They are up-to-date, so running 3.4.2.

The problem is:

Using Konqueror file manager, whenever I try to enter a directory which contains the "[" character, the directory where I am will stay the same and it will appear the direction of the directory I wanted to enter to in the direction bar. If a remove the "[" form the name, or replace for whatever, I'll be able to enter that directory.

My kernel has built-in native language support for:

<*>   Codepage 437 (United States, Canada)
<*>   ASCII (United States)
<*>   NLS ISO 8859-1  (Latin 1; Western European Languages)
<*>   NLS ISO 8859-15 (Latin 9; Western European Languages with Euro) <- being this one the default.

And cat /etc/environment

LANGUAGE="es_ES:es:en_GB:en"
LANG=es_ES@euro

Just want you to try to reproduce the situation, the only requirement is having a directory named "*[*" and try entering with Konqueror from its parent.

Thank you.

---

### Post by sargo on 2005-08-23
It's a bug, for more information see this thread [http://www.ubuntuforums.org/showthread.php?t=53661](http://www.ubuntuforums.org/showthread.php?t=53661) .

Un saludo...

---

### Post by SGC on 2005-08-23
Its a known bug, and has been fixed after releasing kde 3.4.2. So until the next release of kde the only thing you can do is to add slash \ at the end of the file name in the address bar, so /home/username/folder[1] becomes /home/username/folder[1]/

EDIT: sargo was faster than me  :)

---

### Post by Takis on 2005-08-23
Offtopic:
You may like to remove those Debian repositories from your sources.list . Debian repositories *are not* Ubuntu repositories and have a very good chance of breaking your system.

---

