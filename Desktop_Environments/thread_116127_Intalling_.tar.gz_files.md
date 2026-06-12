---
title: "Intalling .tar.gz files"
date: 2006-01-12
forum: Desktop Environments
---

### Post by ripgut on 2006-01-12
i downloaded opera to my ubuntu desktop, now i need to isntall it, any help would be greatly appreciated it, thank you ;)

---

### Post by dcstar on 2006-01-12
[QUOTE=ripgut]i downloaded opera to my ubuntu desktop, now i need to isntall it, any help would be greatly appreciated it, thank you ;)[/QUOTE]
Is there an issue with installing the one listed in Synaptic?

---

### Post by psychicdragon on 2006-01-12
Opera provides packages for Ubuntu linux. Just go [here]("http://opera.com/download/"), and select Ubuntu from the list.

you can install it (once it's downloaded) with the command **sudo dpkg -i opera***.

---

### Post by aysiu on 2006-01-12
[QUOTE=psychicdragon]Opera provides packages for Ubuntu linux. Just go [here]("http://opera.com/download/"), and select Ubuntu from the list.

you can install it (once it's downloaded) with the command **sudo dpkg -i opera***.[/QUOTE] Don't forget you may have to do this first ```
sudo apt-get install xlibs
```

---

### Post by briancurtin on 2006-01-12
if you end up not following their directions, and want to deal with your tar.gz file, google or the search feature of this site can answer questions such as this

---

### Post by ripgut on 2006-01-12
[QUOTE=aysiu]Don't forget you may have to do this first ```
sudo apt-get install xlibs
```[/QUOTE]
Thank you, and i'm loving the links in your signature.

---

### Post by lamego on 2006-01-12
APT repos are always easier to use, also most of the times they guarantee you have a stable system with compatible components.
You may need to install specific software from .tar.gz that is not available on debian packages (neither APT repos), for such cases you should know .tar.gz are just compressed files "zip alike". 
You can extract them from the command line with: 
tar xzvf file.tar.gz
Or you can do it with the graphical pacakage manager that goes with Ubuntu.

---

### Post by ripgut on 2006-01-12
[QUOTE=lamego]APT repos are always easier to use, also most of the times they guarantee you have a stable system with compatible components.
You may need to install specific software from .tar.gz that is not available on debian packages (neither APT repos), for such cases you should know .tar.gz are just compressed files "zip alike". 
You can extract them from the command line with: 
tar xzvf file.tar.gz
Or you can do it with the graphical pacakage manager that goes with Ubuntu.[/QUOTE]

well, i succesfully extracted it. but i'm geting this:

"vincent@ubuntu:~/Desktop/opera-8.51-20051114.6-shared-qt.i386-en$ sudo dpkg -i opera*
dpkg-deb: `opera' is not a debian format archive
dpkg: error processing opera (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `opera6.adr' is not a debian format archive
dpkg: error processing opera6.adr (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 opera
 opera6.adr"

---

### Post by aysiu on 2006-01-13
You *sudo dpkg -i* only .deb files, not .tar.gz files. Go to Opera and find the Ubuntu or Static Deb package.

---

